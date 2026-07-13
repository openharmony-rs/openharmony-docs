# TextOverflow

Declare how text overflows.

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

When the text overflows its dimensions, the text will not be cropped.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Clip

```TypeScript
Clip = 1
```

When the text overflows its dimensions, the text will be cropped and displayed.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ellipsis

```TypeScript
Ellipsis = 2
```

If the text overflows its dimensions, the text that cannot be displayed shall be replaced by ellipsis.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MARQUEE

```TypeScript
MARQUEE = 3
```

When the text overflows its dimensions, the text will scroll for displaying.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

