# ShadowClipMode

```TypeScript
declare enum ShadowClipMode
```

阴影不填充时的裁切方式。

**起始版本：** 26.1.0

<!--Device-unnamed-declare enum ShadowClipMode--><!--Device-unnamed-declare enum ShadowClipMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOUNDS_SHAPE

```TypeScript
BOUNDS_SHAPE = 1
```

按控件 bounds 范围裁切。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ShadowClipMode-BOUNDS_SHAPE = 1--><!--Device-ShadowClipMode-BOUNDS_SHAPE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT_SHAPE

```TypeScript
DEFAULT_SHAPE = 0
```

按默认形状裁切（优先级顺序：shadowShape &gt; clipShape &gt; 控件 bounds）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ShadowClipMode-DEFAULT_SHAPE = 0--><!--Device-ShadowClipMode-DEFAULT_SHAPE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
