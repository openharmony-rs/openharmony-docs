# CpuUsageHighPolicy

提供CPU高负载事件配置策略的定义。
> **注意：**  
>  
> 该接口被调用后，会将设置值持久化。后续重复调用该接口时，若不设置对应参数，则取上一次系统取用的值。

**起始版本：** 22

<!--Device-hiAppEvent-interface CpuUsageHighPolicy--><!--Device-hiAppEvent-interface CpuUsageHighPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## backgroundLoadThreshold

```TypeScript
backgroundLoadThreshold?: number
```

应用后台CPU高负载异常阈值，阈值范围：[1, 100]，单位：%，默认值：10。若设置值在阈值范围外，系统将取用默认值10。

**说明**：建议取值小于10。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CpuUsageHighPolicy-backgroundLoadThreshold?: int--><!--Device-CpuUsageHighPolicy-backgroundLoadThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## foregroundLoadThreshold

```TypeScript
foregroundLoadThreshold?: number
```

应用前台CPU高负载异常阈值，阈值范围：[1, 100]，单位：%，默认值：30。若设置值在阈值范围外，系统将取用默认值30。

**说明**：建议取值小于30。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CpuUsageHighPolicy-foregroundLoadThreshold?: int--><!--Device-CpuUsageHighPolicy-foregroundLoadThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## perfLogCaptureCount

```TypeScript
perfLogCaptureCount?: number
```

采样栈每日采集次数。一旦系统检测到当前异常日志的采集次数超过设置值，系统仍会正常上报事件，但异常事件中的external_log字段，将不再附加日志文件路径信息。

Debug版本应用，阈值范围：[-1, 100]；

Release版本应用，阈值范围：[0, 20]。

单位：次，默认值：1。

若设置值在阈值范围外，系统将取用默认值1。

**说明**：

1. 值为-1，表示不限制采集日志次数。2. 值为0，表示不采集日志。3. 值大于0，表示每日采集次数上限。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CpuUsageHighPolicy-perfLogCaptureCount?: int--><!--Device-CpuUsageHighPolicy-perfLogCaptureCount?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## threadLoadInterval

```TypeScript
threadLoadInterval?: number
```

应用线程CPU高负载异常检测周期，阈值范围：[5, 3600]，单位：秒，默认值：60。

若设置值在阈值范围外，系统将取用默认值60。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CpuUsageHighPolicy-threadLoadInterval?: int--><!--Device-CpuUsageHighPolicy-threadLoadInterval?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## threadLoadThreshold

```TypeScript
threadLoadThreshold?: number
```

应用线程CPU高负载异常阈值，阈值范围：[15, 100]，单位：%，默认值：70。若设置值在阈值范围外，系统将取用默认值70。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CpuUsageHighPolicy-threadLoadThreshold?: int--><!--Device-CpuUsageHighPolicy-threadLoadThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

