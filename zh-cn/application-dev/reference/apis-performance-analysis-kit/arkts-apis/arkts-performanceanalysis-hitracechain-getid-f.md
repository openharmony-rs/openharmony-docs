# getId

## 导入模块

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## getId

```TypeScript
function getId(): HiTraceId
```

获取跟踪标识，同步接口。用于在需要传递当前跟踪标识的场景，例如将跟踪标识传递给子线程、传递给其他进程、或者在日志中记录当前跟踪标识。 获取当前线程TLS中的HiTraceId。若当前线程TLS中不存在有效的HiTraceId，返回各属性值均为0的无效HiTraceId。

**起始版本：** 23

<!--Device-hiTraceChain-function getId(): HiTraceId--><!--Device-hiTraceChain-function getId(): HiTraceId-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | 当前线程TLS中的HiTraceId实例。 |

**示例**

```TypeScript
// 开始跟踪，跟踪标志是DEFAULT。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// 若干业务逻辑完成后，获取当前跟踪标识。
let curTraceId = hiTraceChain.getId();
// 同一跟踪链获取的跟踪标识的chainId一定相同。
if (curTraceId.chainId != traceId.chainId) {
// 基于异常场景的处理逻辑。
}
// 若干业务逻辑完成后，结束跟踪。
hiTraceChain.end(traceId);
```

