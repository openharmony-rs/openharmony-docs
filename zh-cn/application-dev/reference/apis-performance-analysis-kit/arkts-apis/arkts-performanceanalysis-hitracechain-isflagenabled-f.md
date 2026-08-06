# isFlagEnabled

## isFlagEnabled

```TypeScript
function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean
```

判断HiTraceId是否启用了跟踪标志flag，同步接口。用于在业务逻辑中根据跟踪标志进行不同处理，例如检查是否启用了INCLUDE\_ASYNC标志以决定是否 等待异步操作完成、检查是否启用了TP\_INFO标志以决定是否打印调试信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hiTraceChain-function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean--><!--Device-hiTraceChain-function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要判断指定跟踪标志是否启用的HiTraceId实例。 |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定的跟踪标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：HiTraceId已启用flag；false：HiTraceId未启用flag。 |

**示例：**

```TypeScript
// 开始跟踪，跟踪标志是INCLUDE_ASYNC。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// enabledIncludeAsyncFlag为true。
let enabledIncludeAsyncFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
if (enabledIncludeAsyncFlag) {
// 基于INCLUDE_ASYNC跟踪标志已设置场景的处理逻辑。
}
// 业务结束，结束跟踪。
hiTraceChain.end(traceId);
```

