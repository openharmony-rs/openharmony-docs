# stringify

## stringify

```TypeScript
function stringify(value: Object | null | undefined): string
```

将ArkTS值转换为JavaScript对象表示法（JSON）字符串。
额外支持Map和Set。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object \| null \| undefined | 是 | 要转换的值。[since 18] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 该值的JSON字符串表示。 |

