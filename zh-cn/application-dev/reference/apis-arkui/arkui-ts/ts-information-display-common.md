# 信息展示公共接口
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

用于修饰组件，为Gauge和DataPanel组件提供投影等视觉信息展示能力的公共接口，支持统一配置投影模糊半径、偏移量等参数，简化多组件投影样式的统一管理，适用于需要为仪表盘、数据面板等组件添加一致投影效果的场景。

>**说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。


## MultiShadowOptions

投影样式。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型 | 只读 | 可选 | 说明 |
| ------------- | ------- | -- | -- | -------- |
| radius | number \| [Resource](ts-types.md#resource) | 否 | 是 | 投影模糊半径。 <br>API version 10及以前，默认值：5<br>API version 11及以后，默认值：20<br>单位：vp <br>取值范围：(0, +∞)。<br>**说明：** <br>设置小于等于0的值时，按默认值显示。|
| offsetX | number \| [Resource](ts-types.md#resource) | 否 | 是 | X轴偏移量。 <br>number类型取值范围不做限制。<br>默认值：5<br>单位：vp |
| offsetY | number \| [Resource](ts-types.md#resource) | 否 | 是 | Y轴偏移量。 <br>number类型取值范围不做限制。<br>默认值：5<br>单位：vp |
