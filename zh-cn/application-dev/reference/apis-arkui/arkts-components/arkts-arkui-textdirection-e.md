# TextDirection

文本排版方向。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LTR

```TypeScript
LTR = 0
```

文本排版方向从左到右。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RTL

```TypeScript
RTL = 1
```

文本排版方向从右到左。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 2
```

文本排版方向遵循组件布局方向。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 3
```

遵循自身实际文本内容的排版方向，如果文本为 RTL（Right-to-Left）类语言（如藏文、维吾尔文），文本排版方向为从右到左。如果为 LTR（Left-to-Right）类语言（如中文、英文），文本排版方向为从左到右。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

