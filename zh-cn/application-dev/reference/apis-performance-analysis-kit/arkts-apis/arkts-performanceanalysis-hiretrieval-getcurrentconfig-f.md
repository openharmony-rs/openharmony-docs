# getCurrentConfig

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## getCurrentConfig

```TypeScript
function getCurrentConfig(): HiRetrievalConfig
```

获取当前应用灰度活动配置。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-hiRetrieval-function getCurrentConfig(): HiRetrievalConfig--><!--Device-hiRetrieval-function getCurrentConfig(): HiRetrievalConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | 当前应用灰度活动配置，包含用户类型、设备类型、设备型号等参数，用于标识和圈选设备参与应用灰度活动。 |

