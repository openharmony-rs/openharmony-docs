# 枚举说明 (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

>**说明：**
>
>本模块首批接口从API version 11开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## IlluminatedType

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值   | 说明                                               |
| ------ | ---- | ------------------------------------------------------ |
| NONE | 0    | 组件不会被照亮。 |
| BORDER | 1    | 组件边缘可以被照亮。 |
| CONTENT | 2    | 组件内容可以被照亮。 |
| BORDER_CONTENT | 3    | 组件边缘和内容可以被照亮。 |
| BLOOM_BORDER | 4    | 组件边缘可以被照亮，边缘带有发光效果。 |
| BLOOM_BORDER_CONTENT | 5    | 组件边缘和内容可以被照亮，边缘带有发光效果。 |

## ColorSpace<sup>20+</sup>

定义了颜色空间的类型，用于指定颜色显示的模式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称    |  值   | 说明                   |
| ------  | ---- | -------------------- |
| BT2020<sup>24+</sup> | 2 | BT2020颜色空间，具有更广的色域，适用于高端显示设备。 <br/>**模型约束：** 此接口仅可在Stage模型下使用。 <br/>**系统接口：** 此接口为系统接口。 <br/>**ArkTS-Dyn起始版本：** 24 <br/>**ArkTS-Sta起始版本：** 24 |

## EdgeLightPosition枚举说明

边缘流光位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

| 名称           | 值  | 说明                         |
| -------------- | --- |---------------------------- |
| TOP_LEFT       | 0   | 边缘流光在左上角。            |
| TOP_RIGHT      | 1   | 边缘流光在右上角。            |
| BOTTOM_LEFT    | 2   | 边缘流光在左下角。            |
| BOTTOM_RIGHT   | 3   | 边缘流光在右下角。            |
| TOP            | 4   | 边缘流光在顶部。              |
| BOTTOM         | 5   | 边缘流光在底部。              |
| LEFT           | 6   | 边缘流光在左边。              |
| RIGHT          | 7   | 边缘流光在右边。              |
