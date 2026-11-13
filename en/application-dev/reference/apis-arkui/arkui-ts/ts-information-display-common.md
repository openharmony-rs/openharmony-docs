# Information Display APIs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8aa8522c1582655206875d9c89c21656113a2dda translatedAt=2026-11-03T02:45:21.527Z pushedAt=2026-11-13T01:06:00.012Z nl=1 -->

Provides a common interface for modifying components to offer visual information display capabilities such as shadows for the **Gauge** and **DataPanel** components. It supports unified configuration of parameters such as the shadow blur radius and offset, simplifying unified management of shadow styles across multiple components. It is applicable to scenarios where consistent shadow effects need to be added to components such as gauges and data panels.

>**NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.


## MultiShadowOptions

Defines shadow style properties.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type| Read-Only| Optional| Description|
| ------------- | ------- | -- | -- | -------- |
| radius | number \| [Resource](ts-types.md#resource) | No | Yes | Blur radius of the shadow. <br>API version 10, default value: **5**<br>API version 11 and later, default value: 20<br>Unit: vp <br>Value range: (0, +∞).<br>**NOTE**<br>If the value is set to less than or equal to 0, the default value is used. |
| offsetX | number \| [Resource](ts-types.md#resource) | No | Yes | Offset on the x-axis. <br>The value range of the number type is not limited.<br>Default value: **5**<br>Unit: vp |
| offsetY | number \| [Resource](ts-types.md#resource) | No | Yes | Offset on the y-axis. <br>The value range of the number type is not limited.<br>Default value: **5**<br>Unit: vp |
