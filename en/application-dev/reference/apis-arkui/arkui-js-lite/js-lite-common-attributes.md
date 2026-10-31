# Universal Attributes

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-07-31T01:11:03.197Z pushedAt=2026-07-31T12:04:26.553Z -->

Universal attributes describe the basic configuration capabilities commonly supported by components, including component IDs, style references, reference relationships, and rendering control. They are applicable to scenarios where the basic appearance and display of components need to be set in a unified manner, helping developers manage the basic attributes of components in a consistent manner.

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
| if | boolean | Whether the element is added or removed. The value **true** indicates that the element is added, and **false** indicates that the element is removed. |
| show | boolean | Whether the element is displayed or hidden. The value **true** indicates that the element is displayed, and **false** indicates that the element is hidden. |

> **NOTE**
>
> Do not set styles in attribute fields.