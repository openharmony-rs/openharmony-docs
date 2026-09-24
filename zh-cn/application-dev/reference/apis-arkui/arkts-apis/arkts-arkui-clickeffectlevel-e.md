# ClickEffectLevel

```TypeScript
declare enum ClickEffectLevel
```

定义点击效果的级别及对应动效参数。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LIGHT

```TypeScript
LIGHT = 0
```

小面积（轻盈），弹簧动效，刚性：410，阻尼：38，初始速度：1，默认缩放比90%。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MIDDLE

```TypeScript
MIDDLE = 1
```

中面积（稳定），弹簧动效，刚性：350，阻尼：35，初始速度：0.5，默认缩放比95%。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HEAVY

```TypeScript
HEAVY = 2
```

大面积（厚重），弹簧动效，刚性：240，阻尼：28，初始速度：0，默认缩放比95%。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
