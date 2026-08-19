# ImageFit

Image display mode.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ImageFit--><!--Device-unnamed-export declare enum ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fill

```TypeScript
Fill = 0
```

Zoom in or out without maintaining the aspect ratio so that the image fills the display boundary.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-Fill = 0--><!--Device-ImageFit-Fill = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain = 1
```

Keep the aspect ratio to zoom out or zoom in so that the image is completely displayed within the display boundary.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-Contain = 1--><!--Device-ImageFit-Contain = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover = 2
```

Keep the aspect ratio to zoom out or zoom in so that both sides of the image are greater than or equal to the display boundary.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-Cover = 2--><!--Device-ImageFit-Cover = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto = 3
```

Adaptive display

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-Auto = 3--><!--Device-ImageFit-Auto = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 5
```

Keep the original size and display it in the center.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-None = 5--><!--Device-ImageFit-None = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ScaleDown

```TypeScript
ScaleDown = 6
```

Keep the aspect ratio displayed, and the image zooms out or remains unchanged.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-ScaleDown = 6--><!--Device-ImageFit-ScaleDown = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_START

```TypeScript
TOP_START = 7
```

Top Start.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-TOP_START = 7--><!--Device-ImageFit-TOP_START = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 8
```

The top is centered horizontally.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-TOP = 8--><!--Device-ImageFit-TOP = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOP_END

```TypeScript
TOP_END = 9
```

Top tail end.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-TOP_END = 9--><!--Device-ImageFit-TOP_END = 9-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 10
```

The starting end is centered longitudinally.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-START = 10--><!--Device-ImageFit-START = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 11
```

Center horizontal and vertical.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-CENTER = 11--><!--Device-ImageFit-CENTER = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 12
```

The tail end is centered longitudinally.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-END = 12--><!--Device-ImageFit-END = 12-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_START

```TypeScript
BOTTOM_START = 13
```

Bottom starting end.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-BOTTOM_START = 13--><!--Device-ImageFit-BOTTOM_START = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 14
```

The bottom is centered horizontally.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-BOTTOM = 14--><!--Device-ImageFit-BOTTOM = 14-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_END

```TypeScript
BOTTOM_END = 15
```

Bottom end.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-BOTTOM_END = 15--><!--Device-ImageFit-BOTTOM_END = 15-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MATRIX

```TypeScript
MATRIX = 16
```

Matrix of Image.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageFit-MATRIX = 16--><!--Device-ImageFit-MATRIX = 16-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

