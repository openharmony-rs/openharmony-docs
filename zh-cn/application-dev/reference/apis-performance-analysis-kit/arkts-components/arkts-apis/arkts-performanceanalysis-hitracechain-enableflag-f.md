# enableFlag

## 导入模块

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## enableFlag

```TypeScript
function enableFlag(id: HiTraceId, flag: HiTraceFlag): void
```

启用HiTraceId中指定的跟踪标志，同步接口。用于在业务流程中动态调整跟踪行为，例如在调试时启用TP_INFO标志以打印埋点信息、在需要跟踪异步调用时启用INCLUDE_ASYNC标志、在需要禁用日志关联时启用DISABLE_LOG标志。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | 是 | 需要启用指定跟踪标志的HiTraceId实例。 |
| flag | [HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md) | 是 | 指定的跟踪标志。 |

**示例**

```TypeScript
// 开始跟踪，跟踪标志是INCLUDE_ASYNC。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// enabledDoNotCreateSpanFlag为false。
let enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// 设置DONOT_CREATE_SPAN跟踪标志。
hiTraceChain.enableFlag(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// enabledDoNotCreateSpanFlag为true。
enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
if (enabledDoNotCreateSpanFlag) {
// 基于DONOT_CREATE_SPAN跟踪标志已设置场景的处理逻辑。
}
// 业务结束，结束跟踪。
hiTraceChain.end(traceId);
```
