# OverlayOptions

Defines the OverlayOptions interface. &lt;strong&gt;NOTE&lt;/strong&gt;:<br> When both align and offset are set, the effects are combined. The overlay is first aligned relative to the component and then offset from its current upper left corner.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OverlayOptions--><!--Device-unnamed-export declare interface OverlayOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

Defines align type.

**类型：** [Alignment](../../apis-arkui/arkts-apis/arkts-arkui-alignment-e.md)

**默认值：** TopStart

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayOptions-align?: Alignment--><!--Device-OverlayOptions-align?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: OverlayOffset
```

Defines offset type.

**类型：** [OverlayOffset](arkts-na-common-overlayoffset-i.md)

**默认值：** - the overlay is in the upper left corner of the component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayOptions-offset?: OverlayOffset--><!--Device-OverlayOptions-offset?: OverlayOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

