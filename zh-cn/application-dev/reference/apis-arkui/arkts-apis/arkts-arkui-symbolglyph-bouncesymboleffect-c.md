# BounceSymbolEffect

BounceSymbolEffect继承自父类SymbolEffect。

**继承/实现关系：** BounceSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-symboleffect-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class BounceSymbolEffect--><!--Device-unnamed-export declare class BounceSymbolEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope, direction?: EffectDirection)
```

ScaleSymbolEffect的构造函数，缩放动效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BounceSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)--><!--Device-BounceSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-symbolglyph-effectscope-e.md) | 否 | 动效范围。<br/>默认值：EffectScope.LAYER |
| direction | [EffectDirection](arkts-arkui-symbolglyph-effectdirection-e.md) | 否 | 动效方向。<br/>默认值：EffectDirection.DOWN |

## direction

```TypeScript
direction?: EffectDirection
```

动效方向。 默认值：EffectDirection.DOWN

**类型：** [EffectDirection](arkts-arkui-symbolglyph-effectdirection-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BounceSymbolEffect-direction?: EffectDirection--><!--Device-BounceSymbolEffect-direction?: EffectDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

动效范围。 默认值：EffectScope.LAYER

**类型：** [EffectScope](arkts-arkui-symbolglyph-effectscope-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BounceSymbolEffect-scope?: EffectScope--><!--Device-BounceSymbolEffect-scope?: EffectScope-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

