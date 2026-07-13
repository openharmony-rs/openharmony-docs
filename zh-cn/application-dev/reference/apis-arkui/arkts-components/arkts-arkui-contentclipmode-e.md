# ContentClipMode

Enum of scrollable containers' content clip mode.

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_ONLY

```TypeScript
CONTENT_ONLY = 0
```

Clip to content rect inside margin & padding.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOUNDARY

```TypeScript
BOUNDARY = 1
```

Clip to scrollable's outer rect, including padding but inside margin.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA

```TypeScript
SAFE_AREA = 2
```

Clip to the safeArea of scrollable container.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

