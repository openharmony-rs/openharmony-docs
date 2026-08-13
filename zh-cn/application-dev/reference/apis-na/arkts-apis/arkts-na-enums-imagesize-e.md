# ImageSize

ImageSize enumeration description

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum ImageSize--><!--Device-unnamed-export declare enum ImageSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto = 2
```

Keep the scale of the original image unchanged.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSize-Auto = 2--><!--Device-ImageSize-Auto = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover = 1
```

Keep the aspect ratio to zoom in or out the image so that both sides of the image are greater than or equal to the display boundary.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSize-Cover = 1--><!--Device-ImageSize-Cover = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain = 0
```

Keep the aspect ratio to zoom out or zoom in so that the image is completely displayed within the display boundary.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSize-Contain = 0--><!--Device-ImageSize-Contain = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FILL

```TypeScript
FILL = 3
```

Zoom in or out without maintaining the aspect ratio so that the image fills the display boundary.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageSize-FILL = 3--><!--Device-ImageSize-FILL = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

