# OverlayManagerOptions

初始化[OverlayManager](arkts-na-arkui-uicontext-uicontext-c.md)时所用参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface OverlayManagerOptions--><!--Device-unnamed-export interface OverlayManagerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## enableBackPressedEvent

```TypeScript
enableBackPressedEvent?: boolean
```

是否支持通过侧滑手势关闭OverlayManager下的ComponentContent，true表示可以通过侧滑关闭，false表示不可以通过侧滑关闭，默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean--><!--Device-OverlayManagerOptions-enableBackPressedEvent?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBackPress

```TypeScript
onBackPress?: OnOverlayBackPressCallback
```

Callback for intercepting back-press events on an overlay. **NOTE：**1. When this callback is registered and **enableBackPressedEvent** is set to **true**, the back-press event will not close the overlay automatically. Instead, the overlay invokes this callback to decide whether the event should be propagated to the underlying components. 2. Return **true** to intercept the event (the event is consumed and will not be passed to lower layers), or **false** to allow the event to propagate through to the components below the overlay.

**类型：** [OnOverlayBackPressCallback](arkts-na-onoverlaybackpresscallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManagerOptions-onBackPress?: OnOverlayBackPressCallback--><!--Device-OverlayManagerOptions-onBackPress?: OnOverlayBackPressCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderRootOverlay

```TypeScript
renderRootOverlay?: boolean
```

是否渲染overlay根节点，true表示渲染overlay根节点，false表示不渲染overlay根节点，默认值为true。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManagerOptions-renderRootOverlay?: boolean--><!--Device-OverlayManagerOptions-renderRootOverlay?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

