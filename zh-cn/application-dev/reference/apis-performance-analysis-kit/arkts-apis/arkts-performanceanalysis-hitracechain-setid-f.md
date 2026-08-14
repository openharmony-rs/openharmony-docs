# setId

## setId

```TypeScript
function setId(id: HiTraceId): void
```

设置跟踪标识，同步接口。用于在需要将外部跟踪标识设置到当前线程的场景，例如从父线程继承跟踪标识、从其他进程接收跟踪标识、从设备间通信获取跟踪 标识。 将给定的HiTraceId设置到当前线程TLS中。若给定的HiTraceId无效，则不执行任何操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hiTraceChain-function setId(id: HiTraceId): void--><!--Device-hiTraceChain-function setId(id: HiTraceId): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | 是 | HiTraceId实例。 |

## 示例

```TypeScript
// 获取当前跟踪链中的跟踪标识。
let traceId = hiTraceChain.getId();
// 将获取的跟踪标识设置为当前traceId。
hiTraceChain.setId(traceId);
```

