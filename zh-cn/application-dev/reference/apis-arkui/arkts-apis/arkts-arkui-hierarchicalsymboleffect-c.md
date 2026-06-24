# HierarchicalSymbolEffect

定义HierarchicalSymbolEffect类，继承自父类SymbolEffect。

**继承/实现关系：** HierarchicalSymbolEffect extends [SymbolEffect](arkts-arkui-symbolglyph-symboleffect-c.md#SymbolEffect)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(fillStyle?: EffectFillStyle)
```

HierarchicalSymbolEffect的构造函数，层级动效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillStyle | EffectFillStyle | 否 | 动效模式。<br/>默认值：EffectFillStyle.CUMULATIVE |

## fillStyle

```TypeScript
fillStyle?: EffectFillStyle
```

动效模式。

默认值：EffectFillStyle.CUMULATIVE

**类型：** EffectFillStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

