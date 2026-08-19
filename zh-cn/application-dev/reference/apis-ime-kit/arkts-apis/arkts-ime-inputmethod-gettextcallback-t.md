# GetTextCallback

```TypeScript
export type GetTextCallback = (length: int) => string
```

'getLeftTextOfCursor' 或 'getRightTextOfCursor' 事件的回调函数。

**起始版本：** 23

<!--Device-inputMethod-export type GetTextCallback = (length: int) => string--><!--Device-inputMethod-export type GetTextCallback = (length: int) => string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | int | 是 | 文本的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | represents the text in edit box. |

