# Universal Attributes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-10T07:54:09.254Z pushedAt=2026-11-10T10:56:10.386Z nl=1 -->

Common attributes are used to describe the basic configuration capabilities supported by components, including the component ID, style reference, reference relationships, and rendering control. They are applicable to scenarios where the basic appearance and display behavior of components need to be set in a unified manner, helping developers manage the basic attributes of components in a consistent way.

## Common Attributes

Common attributes are used to set component identities and appearance.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | string | No| Unique ID of the component.|
| style | string | No| Style declaration of the component.|
| class | string | No| Style class of the component, which is used to refer to a style table.|
| ref | string | No| Reference information of child elements, which is registered with the parent component on **$refs**.|


## Rendering Attributes

Rendering attributes are used to set whether a component is rendered.

| Name| Type| Description|
| -------- | -------- | -------- |
| for | Array | Expands the current element based on the configured data list.|
| if | boolean | Whether the element is added or removed. The value **true** indicates that the current element is added, and **false** indicates the current element is removed. |
| show | boolean | Whether the element is displayed or hidden. The value **true** indicates that the current element is displayed, and **false** indicates the current element is hidden. |

> **NOTE**
>
> Do not set styles in attribute fields.
