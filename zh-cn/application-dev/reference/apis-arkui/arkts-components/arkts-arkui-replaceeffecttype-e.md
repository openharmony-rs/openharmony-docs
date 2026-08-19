# ReplaceEffectType

替换动效类型的枚举值。

**起始版本：** 20

<!--Device-unnamed-declare enum ReplaceEffectType--><!--Device-unnamed-declare enum ReplaceEffectType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEQUENTIAL

```TypeScript
SEQUENTIAL = 0
```

默认替换动效：当前symbol完全消失后，新symbol出现。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceEffectType-SEQUENTIAL = 0--><!--Device-ReplaceEffectType-SEQUENTIAL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CROSS_FADE

```TypeScript
CROSS_FADE = 1
```

快速替换动效：当前symbol淡出的同时，新symbol淡入，产生更流畅、更快速的过渡效果。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceEffectType-CROSS_FADE = 1--><!--Device-ReplaceEffectType-CROSS_FADE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLASH_OVERLAY

```TypeScript
SLASH_OVERLAY = 2
```

禁用动效：用带有斜杠遮罩层的symbol替换当前symbol，通常用于表示禁用或非活动状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceEffectType-SLASH_OVERLAY = 2--><!--Device-ReplaceEffectType-SLASH_OVERLAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

