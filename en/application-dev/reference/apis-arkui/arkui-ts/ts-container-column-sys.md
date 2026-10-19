# Column (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=502e92239007f618b3ae29831890f9b7e0bdd85e translatedAt=2026-08-21T02:21:29.005Z pushedAt=2026-08-21T07:07:36.436Z -->

A container that lays out child components along the vertical direction. The **Column** component arranges child components vertically in sequence, and supports setting attributes such as alignment and spacing, simplifying the implementation of vertical layouts. It is suitable for various scenarios such as forms, list items, and vertical navigation.

> **NOTE**
>
> - This component is supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For other public APIs, see [Column](ts-container-column.md).

## Attributes

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Adds a point light effect to the **Column** component, affecting the lighting rendering of surrounding components marked as illuminable. A point light is a light source that emits light in all directions from a specific position, and can be used to enhance the three-dimensional appearance and visual depth of the UI. You can configure parameters such as the light position, color, and intensity through **PointLightStyle**. For details, see [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes   | Point light style used to set the UI effect of a point light illuminating surrounding components. Only the **Image**, **Column**, **Flex**, **Row**, and **Stack** components support the point light setting. |