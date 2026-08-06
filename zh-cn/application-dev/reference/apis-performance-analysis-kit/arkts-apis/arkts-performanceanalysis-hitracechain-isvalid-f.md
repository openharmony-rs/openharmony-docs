# isValid

## isValid

```TypeScript
function isValid(id: HiTraceId): boolean
```

判断HiTraceId是否有效，同步接口。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hiTraceChain-function isValid(id: HiTraceId): boolean--><!--Device-hiTraceChain-function isValid(id: HiTraceId): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 需要判断是否有效的HiTraceId实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：HiTraceId有效；false：HiTraceId无效。 |

**示例：**

```TypeScript
// 开始跟踪，跟踪标志是DEFAULT。
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// traceIdIsvalid为true
let traceIdIsvalid = hiTraceChain.isValid(traceId);
if (traceIdIsvalid) {
// 基于跟踪标识合法性校验成功的场景的处理逻辑。
}
// 业务结束，结束跟踪。
hiTraceChain.end(traceId);
```

