# DisappearSymbolEffect

定义DisappearSymbolEffect类，继承自父类SymbolEffect。

**继承/实现关系：** DisappearSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**起始版本：** 12

<!--Device-unnamed-declare class DisappearSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class DisappearSymbolEffect extends SymbolEffect-End-->

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

<!--Device-DisappearSymbolEffect-constructor(scope?: EffectScope)--><!--Device-DisappearSymbolEffect-constructor(scope?: EffectScope)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scope | [EffectScope](arkts-arkui-effectscope-e.md) | 否 | 动效范围。<br/>默认值：EffectScope.LAYER |

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

<!--Device-DisappearSymbolEffect-scope?: EffectScope--><!--Device-DisappearSymbolEffect-scope?: EffectScope-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

