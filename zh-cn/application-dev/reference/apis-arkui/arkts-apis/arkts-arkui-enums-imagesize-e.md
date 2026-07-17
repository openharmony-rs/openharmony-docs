# ImageSize

ImageSize enumeration description

**起始版本：** 7

<!--Device-unnamed-declare enum ImageSize--><!--Device-unnamed-declare enum ImageSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

Keep the scale of the original image unchanged.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSize-Auto--><!--Device-ImageSize-Auto-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover
```

Keep the aspect ratio to zoom in or out the image so that both sides of the image are greater than or equal to the display boundary.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSize-Cover--><!--Device-ImageSize-Cover-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain
```

Keep the aspect ratio to zoom out or zoom in so that the image is completely displayed within the display boundary.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSize-Contain--><!--Device-ImageSize-Contain-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FILL

```TypeScript
FILL = 3
```

Zoom in or out without maintaining the aspect ratio so that the image fills the display boundary.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSize-FILL = 3--><!--Device-ImageSize-FILL = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

