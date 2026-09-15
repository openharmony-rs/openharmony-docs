# Stack (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

堆叠容器，子组件按入栈顺序依次叠加，后入栈的子组件覆盖先入栈的子组件。适用于浮层、弹窗、加载遮罩等需要在同一区域内叠加显示多个子组件的场景。配合定位属性可实现绝对定位布局，精确控制子组件位置，满足复杂UI层次关系的布局需求。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 7开始支持。后续版本如有新增内容将采用上角标单独标记该内容的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[Stack](ts-container-stack.md)。

## 属性

### pointLight<sup>11+</sup>

ArkTS-Dyn: pointLight(value: PointLightStyle)

ArkTS-Sta: pointLight(value: PointLightStyle | undefined)

设置点光源样式，用于为Stack组件添加点光源效果，影响其堆叠子组件的光照渲染。点光源是从特定位置向四周发射光线的光源类型，可用于增强UI界面的立体感和视觉层次。通过PointLightStyle可配置光源的位置、颜色、强度等参数。详细信息请参见[PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle)对象说明。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 参数类型                                                         | 只读 | 可选 | 说明         |
| ------ | ------------------------------------------------------------ | ---- |---- | ------------ |
| value  | ArkTS-Dyn: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle)<br/>ArkTS-Sta: [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) \| undefined | 否 | 否   | 点光源样式，用于设置点光源照亮周围组件的UI效果，影响组件的光照渲染。PointLightStyle对象包含光源位置、颜色、强度等参数，具体配置方式详见链接说明。仅Image、Column、Flex、Row、Stack组件支持设置点光源。<br/>取值为undefined时，与不设置表现一致。 |
