# Stack (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=502e92239007f618b3ae29831890f9b7e0bdd85e translatedAt=2026-08-19T07:28:18.876Z pushedAt=2026-08-20T10:45:03.059Z -->

Defines a stack container where child components are successively stacked in the order they are added, and the latter one overwrites the previous one. It is suitable for scenarios where multiple child components need to be overlaid in the same area, such as floating layers, dialog boxes, and loading masks. When used with positioning attributes, it implements absolute positioning layout to precisely control the positions of child components, meeting the layout requirements of complex UI hierarchies.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For details, see [Stack](ts-container-stack.md).

## Attributes

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Sets the point light style to add a point light effect to the **Stack** component, affecting the lighting rendering of its stacked child components. A point light is a light source that emits light in all directions from a specific position, and can be used to enhance the three-dimensional appearance and visual depth of the UI. You can configure parameters such as the light position, color, and intensity through **PointLightStyle**. For details, see [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes   | Point light style, used to set the UI effect of a point light illuminating surrounding components, affecting the lighting rendering of components. The **PointLightStyle** object contains parameters such as the light source position, color, and intensity. For details about the configuration, see the link. Only the **Image**, **Column**, **Flex**, **Row**, and **Stack** components support setting a point light. |