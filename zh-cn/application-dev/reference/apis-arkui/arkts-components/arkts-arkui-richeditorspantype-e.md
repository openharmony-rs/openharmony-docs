# RichEditorSpanType

Span类型信息。

**起始版本：** 10

<!--Device-unnamed-declare enum RichEditorSpanType--><!--Device-unnamed-declare enum RichEditorSpanType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEXT

```TypeScript
TEXT = 0
```

Span类型为文字。

 

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSpanType-TEXT = 0--><!--Device-RichEditorSpanType-TEXT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## IMAGE

```TypeScript
IMAGE = 1
```

Span类型为图像。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSpanType-IMAGE = 1--><!--Device-RichEditorSpanType-IMAGE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MIXED

```TypeScript
MIXED = 2
```

Span类型为图文混合。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSpanType-MIXED = 2--><!--Device-RichEditorSpanType-MIXED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BUILDER

```TypeScript
BUILDER = 3
```

Span类型为BuilderSpan。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSpanType-BUILDER = 3--><!--Device-RichEditorSpanType-BUILDER = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 4
```

注册此类型的菜单，但未注册TEXT、IMAGE、MIXED、BUILDER菜单时，文字类型、图像类型、图文混合类型、BuilderSpan类型都会触发并显示此类型对应的菜单。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSpanType-DEFAULT = 4--><!--Device-RichEditorSpanType-DEFAULT = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

