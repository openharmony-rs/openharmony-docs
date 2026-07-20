# HierarchicalSymbolEffect

定义HierarchicalSymbolEffect类，继承自父类SymbolEffect。

**继承/实现关系：** HierarchicalSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**起始版本：** 12

<!--Device-unnamed-declare class HierarchicalSymbolEffect extends SymbolEffect--><!--Device-unnamed-declare class HierarchicalSymbolEffect extends SymbolEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(fillStyle?: EffectFillStyle)
```

HierarchicalSymbolEffect的构造函数，层级动效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-HierarchicalSymbolEffect-constructor(fillStyle?: EffectFillStyle)--><!--Device-HierarchicalSymbolEffect-constructor(fillStyle?: EffectFillStyle)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillStyle | [EffectFillStyle](arkts-arkui-effectfillstyle-e.md) | 否 | 动效模式。<br/>默认值：EffectFillStyle.CUMULATIVE |

## fillStyle

```TypeScript
fillStyle?: EffectFillStyle
```

动效模式。

默认值：EffectFillStyle.CUMULATIVE

**类型：** EffectFillStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-HierarchicalSymbolEffect-fillStyle?: EffectFillStyle--><!--Device-HierarchicalSymbolEffect-fillStyle?: EffectFillStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

