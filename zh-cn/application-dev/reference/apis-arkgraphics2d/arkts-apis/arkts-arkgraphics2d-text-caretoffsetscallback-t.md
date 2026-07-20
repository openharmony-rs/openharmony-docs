# CaretOffsetsCallback

```TypeScript
type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean
```

将文本行中每个字符的偏移量和索引值作为参数的回调方法。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-text-type CaretOffsetsCallback = (offset: double, index: int, leadingEdge: boolean) => boolean--><!--Device-text-type CaretOffsetsCallback = (offset: double, index: int, leadingEdge: boolean) => boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | Offset of each character in a text line. The value is a floating point number.  |
| index | number | 是 | Index of each character in a text line. The value is an integer.  |
| leadingEdge | boolean | 是 | Whether the cursor is located at the front of the character. The value true means that the cursor is located at the front of the character, that is, the offset does not contain the character width. The value false means that the cursor is located at the rear of the character, that is, the offset contains the character width.  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否停止调用该回调函数，true表示停止调用该回调函数，false表示继续调用该回调函数。  |

