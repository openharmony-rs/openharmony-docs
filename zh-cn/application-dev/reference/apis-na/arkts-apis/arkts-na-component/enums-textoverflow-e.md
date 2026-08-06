# TextOverflow

Declare how text overflows.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum TextOverflow--><!--Device-unnamed-export declare enum TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

When the text overflows its dimensions, the text will not be cropped.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextOverflow-None = 0--><!--Device-TextOverflow-None = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Clip

```TypeScript
Clip = 1
```

When the text overflows its dimensions, the text will be cropped and displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextOverflow-Clip = 1--><!--Device-TextOverflow-Clip = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ellipsis

```TypeScript
Ellipsis = 2
```

If the text overflows its dimensions, the text that cannot be displayed shall be replaced by ellipsis.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextOverflow-Ellipsis = 2--><!--Device-TextOverflow-Ellipsis = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MARQUEE

```TypeScript
MARQUEE = 3
```

When the text overflows its dimensions, the text will scroll for displaying.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextOverflow-MARQUEE = 3--><!--Device-TextOverflow-MARQUEE = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

