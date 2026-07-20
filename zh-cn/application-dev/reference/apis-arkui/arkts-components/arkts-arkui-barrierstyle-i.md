# BarrierStyle

barrier参数，用于定义一条barrier的id、方向和生成时所依赖的组件。

**起始版本：** 12

<!--Device-unnamed-declare interface BarrierStyle--><!--Device-unnamed-declare interface BarrierStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : BarrierDirection
```

指定barrier的方向。</br>垂直方向（TOP，BOTTOM）的barrier仅能作为组件的水平方向锚点，用作垂直方向锚点时值为0；水平方向（LEFT，RIGHT）的barrier仅能作为组件的垂直方向锚点，用作水平方向锚点时值为0。

默认值：BarrierDirection.LEFT

非法值：按默认值处理。

**类型：** BarrierDirection

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BarrierStyle-direction : BarrierDirection--><!--Device-BarrierStyle-direction : BarrierDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

barrier的id，必须是唯一的并且不可与容器内组件重名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BarrierStyle-id : string--><!--Device-BarrierStyle-id : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## referencedId

```TypeScript
referencedId : Array<string>
```

指定生成barrier所依赖的组件。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BarrierStyle-referencedId : Array<string>--><!--Device-BarrierStyle-referencedId : Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

