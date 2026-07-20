# GuideLineStyle

guideLine参数，用于定义一条guideLine的id、方向和位置。

**起始版本：** 12

<!--Device-unnamed-declare interface GuideLineStyle--><!--Device-unnamed-declare interface GuideLineStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction : Axis
```

指定guideLine的方向。</br> 垂直方向的guideLine仅能作为组件水平方向的锚点，作为垂直方向的锚点时值为0；水平方向的guideLine仅能作为组件垂直方向的锚点，作为水平方向的锚点时值为0。</br>默认值：Axis.Vertical

非法值：按默认值处理。

**类型：** Axis

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GuideLineStyle-direction : Axis--><!--Device-GuideLineStyle-direction : Axis-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id : string
```

guideLine的id，必须是唯一的并且不可与容器内组件重名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GuideLineStyle-id : string--><!--Device-GuideLineStyle-id : string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position : GuideLinePosition
```

指定guideLine的位置。</br>当未声明或声明异常值（如undefined）时，guideLine的位置默认为start: 0。start和end两种声明方式选择一种即可。若同时声明，仅start生效。若容器在某个方向的size被声明为"auto"，则该方向上guideLine的位置只能使用start方式声明（不允许使用百分比）。

默认值：

{

start: 0

}

非法值：按默认值处理。

**类型：** GuideLinePosition

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GuideLineStyle-position : GuideLinePosition--><!--Device-GuideLineStyle-position : GuideLinePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

