# 枚举说明 (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

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
