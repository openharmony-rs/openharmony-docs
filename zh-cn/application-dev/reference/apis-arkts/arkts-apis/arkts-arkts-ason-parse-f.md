# parse

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null
```

将JavaScript对象表示法（JSON）字符串转换为ArkTS值。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串。 |
| reviver | Transformer | 否 | 转换结果的函数。 |
| options | ParseOptions | 否 | 解析的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ISendable | 返回ArkTS值。 |

