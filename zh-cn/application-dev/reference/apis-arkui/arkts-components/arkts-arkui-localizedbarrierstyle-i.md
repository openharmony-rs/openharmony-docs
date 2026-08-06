# LocalizedBarrierStyle

barrier参数，用于定义一条支持镜像模式的barrier的id、方向和生成时所依赖的组件，子组件可通过barrier的id引用屏障作为锚点进行对齐定位。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface LocalizedBarrierStyle--><!--Device-unnamed-declare interface LocalizedBarrierStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

barrier的id，用于标识屏障，子组件可通过此id引用该屏障作为锚点。必须是唯一的并且不可与容器内组件重名。

**类型：** string

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedBarrierStyle-id : string--><!--Device-LocalizedBarrierStyle-id : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedDirection

```TypeScript
localizedDirection : LocalizedBarrierDirection
```

指定barrier的方向。 水平屏障线（TOP/BOTTOM）仅能作为组件垂直方向锚点（top或bottom），用于水平方向锚点时位置视为0。垂直屏障线（START/END，支持LTR/RTL镜像）仅能作为组件水平方向锚点（start或end），用于垂直方向 锚点时位置视为0。 默认值：LocalizedBarrierDirection.START 非法值：按默认值处理。

**类型：** LocalizedBarrierDirection

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedBarrierStyle-localizedDirection : LocalizedBarrierDirection--><!--Device-LocalizedBarrierStyle-localizedDirection : LocalizedBarrierDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

指定生成barrier所依赖的组件。将需要作为屏障基准的组件id放入数组，至少包含一个有效组件ID，不存在的ID会被忽略。支持镜像模式的屏障根据LTR/RTL模式下的实际位置计算屏障位置。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedBarrierStyle-referencedId : Array<string>--><!--Device-LocalizedBarrierStyle-referencedId : Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

