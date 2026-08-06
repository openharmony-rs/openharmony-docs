# OverlayOptions

Defines the OverlayOptions interface. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_:\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ When both align and offset are set, the effects are combined. The overlay is first aligned relative to the component and then offset from its current upper left corner.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OverlayOptions--><!--Device-unnamed-export declare interface OverlayOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

Defines align type.

**类型：** Alignment

**默认值：** TopStart

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayOptions-align?: Alignment--><!--Device-OverlayOptions-align?: Alignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: OverlayOffset
```

Defines offset type.

**类型：** OverlayOffset

**默认值：** - the overlay is in the upper left corner of the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayOptions-offset?: OverlayOffset--><!--Device-OverlayOptions-offset?: OverlayOffset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

