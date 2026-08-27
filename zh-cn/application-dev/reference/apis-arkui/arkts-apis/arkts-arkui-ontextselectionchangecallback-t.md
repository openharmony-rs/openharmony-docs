# OnTextSelectionChangeCallback

```TypeScript
declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void
```

文本选择的位置发生变化或编辑状态下光标位置发生变化时，触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 文本选择区域的起始位置。 |
| selectionEnd | number | 是 | 文本选择区域的结束位置。 |
