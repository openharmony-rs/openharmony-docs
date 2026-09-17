# clearId

## 导入模块

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## clearId

```TypeScript
function clearId(): void
```

清除跟踪标识，同步接口。用于在需要切断当前跟踪链的场景，例如业务逻辑分支不再需要跟踪、任务完成后清理跟踪标识、或者在开始新的跟踪前清理旧的跟踪标识。

将当前线程TLS中的HiTraceId设置为无效。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**示例**

```TypeScript
// 业务开始前，尝试清除跟踪标识。
hiTraceChain.clearId();
// 开始跟踪，跟踪标志是DEFAULT。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// 若干业务逻辑完成后，结束跟踪。
hiTraceChain.end(traceId);
```
