# LineBreakStrategy

Enum of line break strategy

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GREEDY

```TypeScript
GREEDY = 0
```

By default. Display as many characters as possible on each line until no more characters
can be displayed on that line, and do not automatically add hyphens under this strategy

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HIGH_QUALITY

```TypeScript
HIGH_QUALITY = 1
```

High quality folding. Optimize the layout of the entire text's line breaks and automatically
add hyphens if necessary.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BALANCED

```TypeScript
BALANCED = 2
```

Balanced folding. We will try our best to ensure that the width of each line in a paragraph
is the same, and if necessary, we will add conjunction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

