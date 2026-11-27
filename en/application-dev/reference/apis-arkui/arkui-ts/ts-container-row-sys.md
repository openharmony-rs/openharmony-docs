# Row (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @camlostshi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=eb72b2b287c105d9e2c131ea3e695cbf188b1b71 translatedAt=2026-11-17T04:18:04.655Z pushedAt=2026-11-19T08:20:04.888Z nl=1 -->

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
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes   | Point light style, used to set the UI effect of a point light illuminating surrounding components. The **PointLightStyle** object includes parameters such as light position, color, and intensity. For the specific configuration method, see the link description. Only the **Image**, **Column**, **Flex**, **Row**, and **Stack** components support setting a point light. |

