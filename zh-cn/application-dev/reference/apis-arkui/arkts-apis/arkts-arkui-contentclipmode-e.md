# ContentClipMode

```TypeScript
declare enum ContentClipMode
```

Enum of scrollable containers' content clip mode.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_ONLY

```TypeScript
CONTENT_ONLY = 0
```

Clip to content rect inside margin & padding.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BOUNDARY

```TypeScript
BOUNDARY = 1
```

Clip to scrollable's outer rect, including padding but inside margin.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA

```TypeScript
SAFE_AREA = 2
```

Clip to the safeArea of scrollable container.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

