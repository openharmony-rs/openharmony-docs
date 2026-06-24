# OverlayManagerOptions

初始化[OverlayManager](arkts-arkui-uicontext.md)时所用参数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableBackPressedEvent

```TypeScript
enableBackPressedEvent?: boolean
```

是否支持通过侧滑手势关闭OverlayManager下的ComponentContent，true表示可以通过侧滑关闭，false表示不可以通过侧滑关闭，默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderRootOverlay

```TypeScript
renderRootOverlay?: boolean
```

是否渲染overlay根节点，true表示渲染overlay根节点，false表示不渲染overlay根节点，默认值为true。

**类型：** boolean

**默认值：** true

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

