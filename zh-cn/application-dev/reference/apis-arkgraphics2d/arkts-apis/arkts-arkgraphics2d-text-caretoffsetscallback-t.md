# CaretOffsetsCallback

```TypeScript
type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean
```

将文本行中每个字符的偏移量和索引值作为参数的回调方法。

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-text-type CaretOffsetsCallback = (offset: double, index: int, leadingEdge: boolean) => boolean--><!--Device-text-type CaretOffsetsCallback = (offset: double, index: int, leadingEdge: boolean) => boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 文本行中每个字符的偏移量，浮点数，单位为物理像素px。 |
| index | number | 是 | 文本行中每个字符的索引值，整数。 |
| leadingEdge | boolean | 是 | 光标是否位于字符的前缘，true表示位于字符前缘，即偏移量不包含该字符宽度，false表示位于字符后缘，即偏移量包含该字符宽度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否停止调用该回调函数，true表示停止调用该回调函数，false表示继续调用该回调函数。 |
