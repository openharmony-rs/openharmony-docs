# ReplaceEffectType

Symbol的替换效果类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ReplaceEffectType--><!--Device-unnamed-export declare enum ReplaceEffectType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEQUENTIAL

```TypeScript
SEQUENTIAL = 0
```

顺序替换动效，当前符号完全消失后新符号淡入。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReplaceEffectType-SEQUENTIAL = 0--><!--Device-ReplaceEffectType-SEQUENTIAL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CROSS_FADE

```TypeScript
CROSS_FADE = 1
```

交叉淡入淡出动效，当前符号淡出的同时新符号淡入。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReplaceEffectType-CROSS_FADE = 1--><!--Device-ReplaceEffectType-CROSS_FADE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLASH_OVERLAY

```TypeScript
SLASH_OVERLAY = 2
```

斜线覆盖替换动效，用带有斜线的符号替换当前符号，通常用于表示禁用或非活跃状态。如果不存在对应的斜线符号变体，则不播放动画直接替换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReplaceEffectType-SLASH_OVERLAY = 2--><!--Device-ReplaceEffectType-SLASH_OVERLAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

