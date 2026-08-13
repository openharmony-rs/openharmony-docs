# remove

## remove

```TypeScript
function remove(obj: object, property: string): void
```

从ArkTS对象中删除某种属性，可用于[JSON.parse](arkts-arkts-json-parse-f.md#parse)解析JSON字符串之后，如清理敏感字段、移除冗余数据等场景。 JSON.remove接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function remove(obj: object, property: string): void--><!--Device-json-function remove(obj: object, property: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ArkTS对象，仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串解析后的对象。 |
| property | string | 是 | 要删除的属性名称，用于指定需从ArkTS对象中移除的属性。 |

