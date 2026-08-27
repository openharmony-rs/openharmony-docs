# GuideLineStyle

guideLine参数，用于定义一条guideLine的id、方向和位置，辅助子组件在RelativeContainer中进行定位和对齐。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## direction

```TypeScript
direction : Axis
```

指定guideLine的方向。Axis.Vertical表示垂直辅助线，仅能作为组件水平方向的锚点；Axis.Horizontal表示水平辅助线，仅能作为组件垂直方向的锚点。默认值：Axis.Vertical非法值：按默认值处理。

**类型：** Axis

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

guideLine的id，用于标识辅助线，子组件可通过此id引用该辅助线作为锚点。必须是唯一的并且不可与容器内组件重名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position : GuideLinePosition
```

指定guideLine的位置。当未声明或声明异常值（如undefined）时，guideLine的位置默认为start: 0。start和end两种声明方式选择一种即可。若同时声明，仅start生效。若容器的width被声明为"auto"，则 Axis.Vertical类型guideLine的位置只能使用start方式声明（不允许使用百分比）；若容器的height被声明为"auto"，则Axis.Horizontal类型guideLine的位置只能使用start方式声明 （不允许使用百分比）。默认值：{start: 0}非法值：按默认值处理。

**类型：** [GuideLinePosition](arkts-arkui-guidelineposition-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
