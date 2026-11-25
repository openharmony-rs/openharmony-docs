# Flex (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=eb72b2b287c105d9e2c131ea3e695cbf188b1b71 translatedAt=2026-11-17T03:52:45.278Z pushedAt=2026-11-19T08:20:04.855Z nl=1 -->

A container component that lays out child components in a flexible manner. The **Flex** component provides flexible layout capabilities, supporting the arrangement and alignment of child components along the main axis (the primary direction in which child components are arranged) and the cross axis (the direction perpendicular to the main axis). It is suitable for scenarios requiring dynamic layout adjustment and responsive interface design. For details, see [Flex](ts-container-flex.md).

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For details, see [Flex](ts-container-flex.md).

## Attributes

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Sets the point light style to the **Flex** component, affecting the lighting rendering of surrounding components marked as illuminable. Parameters such as the position, color, and intensity of the light source can be configured through **PointLightStyle**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes   | Point light style, used to set the position, color, intensity, and other attributes of the light source, affecting the lighting effect of the component. Only the **Image**, **Column**, **Flex**, **Row**, and **Stack** components support setting a point light. |


