# 使用 statsmodels 和 Prophet 进行时间序列预测

> 原文：[`www.kdnuggets.com/2023/03/time-series-forecasting-statsmodels-prophet.html`](https://www.kdnuggets.com/2023/03/time-series-forecasting-statsmodels-prophet.html)

![使用 statsmodels 和 Prophet 进行时间序列预测](img/4a5c14cb8db13d4f46524c0ca6b33b11.png)

图片来源于 [jcomp](https://www.freepik.com/free-vector/businessmen-invest-market-gain-success-from-investing_27306158.htm#query=forecast&position=6&from_view=search&track=sph#position=6&query=forecast) 在 [Freepik](https://www.freepik.com/)

时间序列是一种在数据科学领域独特的数据集。数据是按时间频率（例如：每日、每周、每月等）记录的，每个观察值与其他观察值相关。时间序列数据在你想分析数据随时间变化的情况并进行未来预测时非常有价值。

* * *

## 我们的前 3 个课程推荐

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 1\. [Google 网络安全证书](https://www.kdnuggets.com/google-cybersecurity) - 快速通道进入网络安全职业。

![](img/e225c49c3c91745821c8c0368bf04711.png) 2\. [Google 数据分析专业证书](https://www.kdnuggets.com/google-data-analytics) - 提升你的数据分析技能

![](img/0244c01ba9267c002ef39d4907e0b8fb.png) 3\. [Google IT 支持专业证书](https://www.kdnuggets.com/google-itsupport) - 支持你的组织的 IT

* * *

时间序列预测是一种基于历史时间序列数据创建未来预测的方法。时间序列预测有许多统计方法，例如 [ARIMA](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average) 或 [指数平滑](https://en.wikipedia.org/wiki/Exponential_smoothing)。

时间序列预测在商业中经常遇到，因此数据科学家了解如何开发时间序列模型是非常有益的。在本文中，我们将学习如何使用两个流行的预测 Python 包：statsmodels 和 Prophet 来进行时间序列预测。让我们开始吧。

# 使用 statsmodels 进行时间序列预测

[statsmodels](https://www.statsmodels.org/stable/index.html) Python 包是一个开源包，提供了各种统计模型，包括时间序列预测模型。让我们用一个示例数据集来试用这个包。本文将使用来自 Kaggle 的 [数字货币时间序列](https://www.kaggle.com/datasets/ahmedadam415/digital-currency-time-series) 数据（CC0：公共领域）。

让我们清理数据，看看我们拥有的数据集。

```py
import pandas as pd

df = pd.read_csv('dc.csv')

df = df.rename(columns = {'Unnamed: 0' : 'Time'})
df['Time'] = pd.to_datetime(df['Time'])
df = df.iloc[::-1].set_index('Time')

df.head()
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/e2438d8f02379622ea1332c80b63473c.png)

对于我们的示例，假设我们想预测‘close_USD’变量。让我们看看数据随时间的模式。

```py
import matplotlib.pyplot as plt

plt.plot(df['close_USD'])
plt.show()
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/20f95d59228f79f03a7303d94d011edf.png)

让我们基于上述数据构建预测模型。在建模之前，我们先将数据分为训练数据和测试数据。

```py
# Split the data
train = df.iloc[:-200] 
test = df.iloc[-200:]
```

我们不会随机分割数据，因为这是时间序列数据，我们需要保持顺序。相反，我们尝试从较早的数据中获取训练数据，从最新的数据中获取测试数据。

让我们使用 statsmodels 创建一个预测模型。[statsmodel](https://www.statsmodels.org/stable/tsa.html) 提供了许多时间序列模型 API，但我们将使用 ARIMA 模型作为示例。

```py
from statsmodels.tsa.arima.model import ARIMA

#sample parameters
model = ARIMA(train, order=(2, 1, 0)) 
results = model.fit()

# Make predictions for the test set
forecast = results.forecast(steps=200)
forecast 
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/6d8bb1bef7463a9abc255d3504026004.png)

在我们的示例中，我们使用 statsmodels 的 ARIMA 模型作为预测模型，并尝试预测接下来的 200 天。

模型结果好吗？让我们来评估一下。时间序列模型评估通常使用可视化图来比较实际值和预测值，并使用回归指标如均绝对误差 (MAE)、均方根误差 (RMSE) 和均绝对百分比误差 (MAPE)。

```py
from sklearn.metrics import mean_squared_error, mean_absolute_error
import numpy as np

#mean absolute error
mae = mean_absolute_error(test, forecast)

#root mean square error
mse = mean_squared_error(test, forecast)
rmse = np.sqrt(mse)

#mean absolute percentage error
mape = (forecast - test).abs().div(test).mean()

print(f"MAE: {mae:.2f}")
print(f"RMSE: {rmse:.2f}")
print(f"MAPE: {mape:.2f}%")
```

```py
MAE: 7956.23

RMSE: 11705.11

MAPE: 0.35%
```

上述评分看起来不错，但我们来看看它们的可视化效果如何。

```py
plt.plot(train.index, train, label='Train')
plt.plot(test.index, test, label='Test')
plt.plot(forecast.index, forecast, label='Forecast')
plt.legend()
plt.show()
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/287a6cd87f9b674343d562f5b6d2e203.png)

如我们所见，预测效果较差，因为我们的模型无法预测上升趋势。我们使用的 ARIMA 模型似乎过于简单。

也许我们可以尝试使用 statsmodels 之外的其他模型。让我们尝试一下 Facebook 的著名 Prophet 包。

# 使用 Prophet 进行时间序列预测

[Prophet](https://facebook.github.io/prophet/) 是一个时间序列预测模型包，适用于具有季节性影响的数据。Prophet 还被认为是一个稳健的预测模型，因为它可以处理缺失数据和异常值。

让我们试试 Prophet 包。首先，我们需要安装这个包。

```py
pip install prophet
```

之后，我们必须准备数据集以进行预测模型训练。Prophet 有一个特定要求：时间列需要命名为‘ds’，值列需要命名为‘y’。

```py
df_p = df.reset_index()[["Time", "close_USD"]].rename(
    columns={"Time": "ds", "close_USD": "y"}
)
```

数据准备好之后，我们来尝试基于数据创建预测。

```py
import pandas as pd
from prophet import Prophet

model = Prophet()

# Fit the model
model.fit(df_p)

# create date to predict
future_dates = model.make_future_dataframe(periods=365)

# Make predictions
predictions = model.predict(future_dates)

predictions.head() 
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/3d34d319e0a2556190835b0f253327a3.png)

Prophet 的优点在于每个预测数据点都为用户提供了详细的信息。然而，仅从数据中很难理解结果。因此，我们可以尝试使用 Prophet 对其进行可视化。

```py
model.plot(predictions)
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/7d894c1a2dd2a101a478702e2a019f24.png)

模型的预测绘图函数会提供我们对预测的信心程度。从上述图中，我们可以看到预测有上升的趋势，但随着预测时间的延长，不确定性增加。

还可以使用以下函数检查预测组件。

```py
model.plot_components(predictions)
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/35ada67124732d053e9e2b0442ba5590.png)

默认情况下，我们会获得具有年度和每周季节性的数据显示趋势。这是一种很好的方式来解释数据的变化情况。

是否也可以评估 Prophet 模型？当然可以。Prophet 包括一个我们可以使用的诊断测量：[时间序列交叉验证](https://facebook.github.io/prophet/docs/diagnostics.html#cross-validation)。该方法使用历史数据的一部分，每次使用截止点之前的数据拟合模型。然后 Prophet 将预测结果与实际结果进行比较。让我们尝试使用代码。

```py
from prophet.diagnostics import cross_validation, performance_metrics

# Perform cross-validation with initial 365 days for the first training data and the cut-off for every 180 days.

df_cv = cross_validation(model, initial='365 days', period='180 days', horizon = '365 days')

# Calculate evaluation metrics
res = performance_metrics(df_cv)

res 
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/aca174fb6e6da3d9088aed28c1e5389b.png)

在上述结果中，我们获得了每个预测日实际结果与预测结果的评估结果。也可以使用以下代码可视化结果。

```py
from prophet.plot import plot_cross_validation_metric
#choose between 'mse', 'rmse', 'mae', 'mape', 'coverage'

plot_cross_validation_metric(df_cv, metric= 'mape')
```

![使用 statsmodels 和 Prophet 进行时间序列预测](img/1bf2ff18fca3703cab513326672fb7bf.png)

如果我们查看上面的图表，可以看到预测误差随着天数的变化而变化，在某些点可能达到 50%的误差。这样，我们可能需要进一步调整模型以修正误差。你可以查看[文档](https://facebook.github.io/prophet/docs/)以进行进一步探索。

# 结论

预测是商业中常见的情况之一。开发预测模型的一种简单方法是使用 statsforecast 和 Prophet Python 包。本文将介绍如何创建预测模型并使用 statsforecast 和 Prophet 进行评估。

**[Cornellius Yudha Wijaya](https://www.linkedin.com/in/cornellius-yudha-wijaya/)** 是一名数据科学助理经理和数据撰稿人。在全职工作于印尼安联期间，他喜欢通过社交媒体和写作媒体分享 Python 和数据技巧。

### 更多相关话题

+   [使用 Ploomber、Arima、Python 和 Slurm 进行时间序列预测](https://www.kdnuggets.com/2022/03/time-series-forecasting-ploomber-arima-python-slurm.html)

+   [利用 XGBoost 进行时间序列预测](https://www.kdnuggets.com/2023/08/leveraging-xgboost-timeseries-forecasting.html)

+   [解释性预测和最新预测：最先进的深度学习…](https://www.kdnuggets.com/2021/12/sota-explainable-forecasting-and-nowcasting.html)

+   [预测未来事件：AI 和 ML 的能力与局限性](https://www.kdnuggets.com/2023/06/forecasting-future-events-capabilities-limitations-ai-ml.html)

+   [学习现代预测技术以帮助预测未来业务…](https://www.kdnuggets.com/2022/12/sphere-learn-modern-forecasting-techniques-help-predict-future-business-outcomes.html)

+   [市场数据和新闻：时间序列分析](https://www.kdnuggets.com/2022/06/market-data-news-time-series-analysis.html)
