# CaretOffsetsCallback

```TypeScript
type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean
```

将文本行中每个字符的偏移量和索引值作为参数的回调方法。

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | double | 是 | Offset of each character in a text line. The value is a floating point number. |
| index | int | 是 | Index of each character in a text line. The value is an integer. |
| leadingEdge | boolean | 是 | Whether the cursor is located at the front of the character. The value true meansthat the cursor is located at the front of the character, that is, the offset does not contain the characterwidth. The value false means that the cursor is located at the rear of the character, that is, the offsetcontains the character width. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否停止调用该回调函数，true表示停止调用该回调函数，false表示继续调用该回调函数。 |

