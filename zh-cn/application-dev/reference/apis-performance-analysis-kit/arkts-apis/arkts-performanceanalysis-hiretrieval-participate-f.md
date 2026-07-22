# participate

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## participate

```TypeScript
function participate(config: HiRetrievalConfig): void
```

设置此设备参与应用灰度活动。调用后向服务器发送参与灰度消息和应用灰度活动配置，服务器标记此设备为可圈选并记录该应用灰度活动配置作为算法参数。多次调用将更新为最新的应用灰度活动配置。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-hiRetrieval-function participate(config: HiRetrievalConfig): void--><!--Device-hiRetrieval-function participate(config: HiRetrievalConfig): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | 是 | 开发者指定的应用灰度活动配置。用于设置此设备参与应用灰度活动时的用户类型、设备类型和设备型号信息，服务器将记录这些配置作为算法参数，用于圈选设备。不同参数值会影响设备参与应用灰度活动的概率和采集的日志类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 36000001 | Initialization error.Possibly caused by invoking this function before invoking init function. |

