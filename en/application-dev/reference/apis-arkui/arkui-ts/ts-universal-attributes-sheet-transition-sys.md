# Sheet Transition (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

You can bind a sheet to a component through the **bindSheet** attribute. You can also set the sheet to the preset or custom height for when the component is inserted.

>  **NOTE**
>
>  This feature is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
>  Route hopping is not supported.
>
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [bindSheet](./ts-universal-attributes-sheet-transition.md#bindsheet).

## SheetOptions

Optional attributes of the sheet. Inherits from [BindOptions](./ts-universal-attributes-sheet-transition.md#bindoptions).

| Name             | Type                                      | Read-Only| Optional  | Description             |
| --------------- | ------------------------------- | --------- | ---- | --------------- |
| offset<sup>14+</sup>       | [Position](ts-types.md#position) | No| No   | Offset of the sheet. Bottom spacing, which is effective only when the sheet is a bottom sheet. The **detents** property of [SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions) is not supported. This property has no effect when the y-axis value is set to a negative number.<br> Default value: 0 vp for both the x-axis and y-axis<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.ArkUI.ArkUI.Full|
