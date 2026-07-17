# SetPreviewTextCallback

```TypeScript
export type SetPreviewTextCallback = (text: string, range: Range) => void
```

当输入法框架需要显示预览文本时触发的回调。

**起始版本：** 17

<!--Device-inputMethod-export type SetPreviewTextCallback = (text: string, range: Range) => void--><!--Device-inputMethod-export type SetPreviewTextCallback = (text: string, range: Range) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 预览文本内容。 |
| range | Range | 是 | 文本的选中范围。 |

