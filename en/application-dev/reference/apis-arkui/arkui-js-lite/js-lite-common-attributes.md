# Universal Attributes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7b6b884ef565767a6c9d0d7139fb4cb24a435447 translatedAt=2026-06-05T10:26:30.303Z pushedAt=2026-06-05T12:07:10.884Z -->


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
| if | boolean | Whether the element is added or removed.|
| show | boolean | Whether the element is displayed or hidden.|

> **NOTE**
>
> Do not set styles in attribute fields.