# Row (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=502e92239007f618b3ae29831890f9b7e0bdd85e translatedAt=2026-08-19T07:12:00.653Z pushedAt=2026-08-20T10:45:03.044Z -->

Defines a container that lays out child components horizontally. It is suitable for horizontal arrangement scenarios such as toolbars and navigation bars, and can flexibly control the alignment, spacing, and arrangement order of child components.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For details, see [Row](ts-container-row.md).

## Attributes

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Sets the point light style to add a point light effect to the **Row** component, affecting the lighting rendering of surrounding components marked as illuminable. A point light is a light source that emits light in all directions from a specific position, and can be used to enhance the three-dimensional appearance and visual depth of the UI. You can configure parameters such as the light position, color, and intensity through **PointLightStyle**. For details, see [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes   | Point light style, used to set the UI effect of a point light illuminating surrounding components. The **PointLightStyle** object contains parameters such as the light position, color, and intensity. For details about the configuration, see the link. Only the **Image**, **Column**, **Flex**, **Row**, and **Stack** components support point light settings. |