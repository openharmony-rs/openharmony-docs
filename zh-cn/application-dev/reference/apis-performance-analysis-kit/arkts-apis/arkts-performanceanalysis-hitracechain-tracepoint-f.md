# tracepoint

## tracepoint

```TypeScript
function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void
```

[@ohos.hiTraceMeter (性能打点)]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_跟踪信息埋点，同步接口。 本接口与HiTraceMeter模块协同工作，HiTraceChain负责跟踪链的管理，HiTraceMeter负责性能数据的采集和统计。当type为客户端发送CS且服务端 接收到SR时，进行同步HiTraceMeter开始打点；当type为服务端发送SS且客户端接收到CR时，进行同步HiTraceMeter结束打点；CS和CR以及SR和SS的 信息埋点需配套使用。否则，HiTraceMeter开始与结束打点无法正常匹配；当type为通用类型GENERAL时，不会进行HiTraceMeter打点。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hiTraceChain-function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void--><!--Device-hiTraceChain-function tracepoint(mode: HiTraceCommunicationMode, type: HiTraceTracepointType, id: HiTraceId, msg?: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Communication mode for the trace point. |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 信息埋点需要指定的跟踪埋点类型。 |
| id | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 实施信息埋点操作的HiTraceId实例。 |
| msg | string | 否 | HiTraceMeter打点操作传入的trace说明信息，用于在性能分析时标识打点位置。当需要在HiTraceMeter报告中区分不同打点位置时传入有意义的描述信息（如函数名、操作步骤等），不传入时使用空字符串，不影响基本打点功能。该参数的长度不超过63Byte，超出部分将被截断。 |

**示例：**

```TypeScript
// 开始跟踪，跟踪标志是INCLUDE_ASYNC与DONOT_CREATE_SPAN的并集。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC | hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// 若干业务逻辑完成后，触发信息埋点操作。
hiTraceChain.tracepoint(hiTraceChain.HiTraceCommunicationMode.THREAD, hiTraceChain.HiTraceTracepointType.SS, traceId, "Just an example");
// 业务结束，结束跟踪。
hiTraceChain.end(traceId);
```

