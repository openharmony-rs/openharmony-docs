# ScaleSymbolEffect

ScaleSymbolEffect继承自父类SymbolEffect。

**继承/实现关系：** ScaleSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-symboleffect-c.md#SymbolEffect)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ScaleSymbolEffect--><!--Device-unnamed-export declare class ScaleSymbolEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope, direction?: EffectDirection)
```

ScaleSymbolEffect的构造函数，缩放动效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)--><!--Device-ScaleSymbolEffect-constructor(scope?: EffectScope, direction?: EffectDirection)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-symbolglyph-effectscope-e.md) | 否 | 动效范围。&lt;br/&gt;默认值：EffectScope.LAYER |
| direction | [EffectDirection](arkts-arkui-symbolglyph-effectdirection-e.md) | 否 | 动效方向。&lt;br/&gt;默认值：EffectDirection.DOWN |

## direction

```TypeScript
direction?: EffectDirection
```

动效方向。 默认值：EffectDirection.DOWN

**类型：** [EffectDirection](arkts-arkui-symbolglyph-effectdirection-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleSymbolEffect-direction?: EffectDirection--><!--Device-ScaleSymbolEffect-direction?: EffectDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

动效范围。 默认值：EffectScope.LAYER

**类型：** [EffectScope](arkts-arkui-symbolglyph-effectscope-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleSymbolEffect-scope?: EffectScope--><!--Device-ScaleSymbolEffect-scope?: EffectScope-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

