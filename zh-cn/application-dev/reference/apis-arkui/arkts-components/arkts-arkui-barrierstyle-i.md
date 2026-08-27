# BarrierStyle

barrier参数，用于定义一条barrier的id、方向和生成时所依赖的组件，子组件可通过barrier的id引用屏障作为锚点进行对齐定位。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## direction

```TypeScript
direction : BarrierDirection
```

指定barrier的方向。水平屏障线（TOP/BOTTOM）仅能作为组件垂直方向锚点（top或bottom），用于水平方向锚点时位置视为0。垂直屏障线（LEFT/RIGHT）仅能作为组件水平方向锚点（left或right），用于垂直方向锚点时位置视为0。默认值：BarrierDirection.LEFT非法值：按默认值处理。

**类型：** [BarrierDirection](arkts-arkui-barrierdirection-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

barrier的id，用于标识屏障，子组件可通过此id引用该屏障作为锚点。必须是唯一的并且不可与容器内组件重名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

指定生成barrier所依赖的组件。将需要作为屏障基准的组件id放入数组，至少包含一个有效组件ID，不存在的ID会被忽略。barrier根据组件边界计算位置：LEFT取最左侧，RIGHT取最右侧，TOP取最上方，BOTTOM取最下 方。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
