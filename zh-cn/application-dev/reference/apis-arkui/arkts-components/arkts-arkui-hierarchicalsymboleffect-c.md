# HierarchicalSymbolEffect

HierarchicalSymbolEffect继承自父类SymbolEffect。

**继承/实现关系：** HierarchicalSymbolEffect extends [SymbolEffect](arkts-arkui-symboleffect-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(fillStyle?: EffectFillStyle)
```

HierarchicalSymbolEffect的构造函数，层级动效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fillStyle | [EffectFillStyle](arkts-arkui-effectfillstyle-e.md) | 否 | 动效模式。具体枚举值及说明请参考EffectFillStyle枚举说明。 默认值：EffectFillStyle.CUMULATIVE |

## fillStyle

```TypeScript
fillStyle?: EffectFillStyle
```

动效模式。默认值：EffectFillStyle.CUMULATIVE

**类型：** [EffectFillStyle](arkts-arkui-effectfillstyle-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
