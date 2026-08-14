# RepeatMode

Defines the Border Image Repeat Mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum RepeatMode--><!--Device-unnamed-export declare enum RepeatMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Repeat

```TypeScript
Repeat = 0
```

The source image's slices are tiled. Tiles beyond the border box will be clipped.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RepeatMode-Repeat = 0--><!--Device-RepeatMode-Repeat = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Stretch

```TypeScript
Stretch = 1
```

The source image's slices are stretched to fill the border box.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RepeatMode-Stretch = 1--><!--Device-RepeatMode-Stretch = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Round

```TypeScript
Round = 2
```

The source image's slices are tiled to fill the border box. Tiles may be compressed when needed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RepeatMode-Round = 2--><!--Device-RepeatMode-Round = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Space

```TypeScript
Space = 3
```

The source image's slices are tiled to fill the border box. Extra space will be distributed in between tiles.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RepeatMode-Space = 3--><!--Device-RepeatMode-Space = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

