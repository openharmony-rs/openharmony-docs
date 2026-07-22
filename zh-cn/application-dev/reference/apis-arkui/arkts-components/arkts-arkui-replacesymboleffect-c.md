# ReplaceSymbolEffect

定义ReplaceSymbolEffect类，继承自父类SymbolEffect。

**继承/实现关系：** ReplaceSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**起始版本：** 12

<!--Device-unnamed-declare class ReplaceSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class ReplaceSymbolEffect extends SymbolEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(scope?: EffectScope)
```

AppearSymbolEffect的构造函数，出现动效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope)--><!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-effectscope-e.md) | 否 | 动效范围。<br/>默认值：EffectScope.LAYER |

## constructor

```TypeScript
constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)
```

ReplaceSymbolEffect的构造函数，替换动效。支持指定具体的替换动效类型。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)--><!--Device-ReplaceSymbolEffect-constructor(scope?: EffectScope, replaceType?: ReplaceEffectType)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-effectscope-e.md) | 否 | 动效范围。<br/>默认值：EffectScope.LAYER |
| replaceType | [ReplaceEffectType](arkts-arkui-replaceeffecttype-e.md) | 否 | 替换动效类型。<br/>默认值：ReplaceEffectType.SEQUENTIAL |

## replaceType

```TypeScript
replaceType?: ReplaceEffectType
```

替换动效类型。

默认值：ReplaceEffectType.SEQUENTIAL

**类型：** ReplaceEffectType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceSymbolEffect-replaceType?: ReplaceEffectType--><!--Device-ReplaceSymbolEffect-replaceType?: ReplaceEffectType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scope

```TypeScript
scope?: EffectScope
```

动效范围。

默认值：EffectScope.LAYER

**类型：** EffectScope

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ReplaceSymbolEffect-scope?: EffectScope--><!--Device-ReplaceSymbolEffect-scope?: EffectScope-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

