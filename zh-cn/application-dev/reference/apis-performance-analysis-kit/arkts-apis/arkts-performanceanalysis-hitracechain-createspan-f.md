# createSpan

## createSpan

```TypeScript
function createSpan(): HiTraceId
```

创建跟踪分支，同步接口。用于在业务流程中标记重要的子流程，例如在请求处理过程中的关键步骤、服务端处理链中的各个阶段、或者需要重点关注的业务 分支。 创建一个HiTraceId，使用当前线程TLS中的chainId、spanId初始化HiTraceId的chainId、parentSpanId，并为HiTraceId生成一个新的spanId， 返回该HiTraceId。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hiTraceChain-function createSpan(): HiTraceId--><!--Device-hiTraceChain-function createSpan(): HiTraceId-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | HiTraceId实例。 |

## 示例

```TypeScript
// 开始跟踪，跟踪标志是DEFAULT。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// 若干业务逻辑完成后，创建跟踪分支。
let spanTraceId = hiTraceChain.createSpan();
// 同一跟踪链的跟踪标识的chainId一定相同。
if (spanTraceId.chainId != traceId.chainId) {
// 基于异常场景的处理逻辑。
}
// 业务结束，结束跟踪。
hiTraceChain.end(traceId);
```

