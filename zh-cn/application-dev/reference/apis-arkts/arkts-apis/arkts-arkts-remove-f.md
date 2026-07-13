# remove

## remove

```TypeScript
function remove(obj: object, property: string): void
```

从ArkTS对象中删除一个键。此API可用于[JSON.parse](arkts-arkts-parse-f.md#parse-1)解析JSON字符串后的相关操作。仅支持最外层为字典格式（大括号而非中括号）的有效JSON字符串。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ArkTS对象。 |
| property | string | 是 | 待删除的键。 |

