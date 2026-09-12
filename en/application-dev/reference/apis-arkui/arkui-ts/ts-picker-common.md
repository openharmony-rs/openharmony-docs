# Picker Common APIs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=23e3af99bbbae5d3ef1af76c14a5ad32ec002e14 translatedAt=2026-09-01T11:37:12.007Z pushedAt=2026-09-02T11:24:46.590Z -->

This topic covers the common APIs of picker components.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

## PickerTextStyle

Defines the text style of the picker component, which is used to configure the appearance attributes of the text displayed in the picker.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


| Name  | Type                                    | Read-Only| Optional| Description                     |
| ----- | ---------------------------------------- | ---- | ------------------------- | ------------------------- |
| color | [ResourceColor](ts-types.md#resourcecolor) | No   | Yes   | Text color, used to customize the color of the text in the picker. Pass this parameter when a specific color is required; otherwise, the system default text color is used.             |
| font  | [Font](ts-types.md#font)                   | No   | Yes   | Text style, including attributes such as font size, font weight, and font family. Pass this parameter when the font style of the text in the picker needs to be customized; otherwise, the system default text style is used. |


## PickerDialogButtonStyle<sup>12+</sup>

Defines the button style of the picker dialog box, which is used to configure the display style, role, and behavior of the confirm and cancel buttons in dialog boxes such as the date picker and time picker.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


| Name  | Type                                    | Read-Only| Optional| Description                     |
| ----- | ---------------------------------------- | ---- | ------------------------- | ------------------------- |
| type            | [ButtonType](ts-basic-components-button.md#buttontype)                   | No   | Yes   | Button display style, used to set the display type of the button. Pass this parameter when you need to customize the button display style; otherwise, the default button display style is used.                                                                                                                                                             |
| style           | [ButtonStyleMode](ts-basic-components-button.md#buttonstylemode11)       | No   | Yes   | Style and importance of the button, used to set the visual style and interaction importance level of the button. Pass this parameter when you need to customize the button style; otherwise, the default button style is used.                                                                                                                                                      |
| role            | [ButtonRole](ts-basic-components-button.md#buttonrole12)                 | No   | Yes   | Button role, used to define the semantic role of the button in the dialog box. The options include Normal and Error. For details, see [ButtonRole](ts-basic-components-button.md#buttonrole12). Default value: **ButtonRole.NORMAL**.                                                                  |
| fontSize        | [Length](ts-types.md#length)                                                 | No   | Yes   | Font size of the text, used to customize the size of the button text. Unit: fp.                                                                                                                                                                                     |
| fontColor       | [ResourceColor](ts-types.md#resourcecolor)                                   | No   | Yes   | Text color, used to customize the color of the button text.                                                                                                                                                                                           |
| fontWeight      | [FontWeight](ts-appendix-enums.md#fontweight)&nbsp;\|&nbsp;number&nbsp;\|&nbsp;string | No   | Yes   | Font weight of the text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font. For the string type, only the string form of the number type value is supported, for example, "200", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in **FontWeight**. Default value: **FontWeight.Normal**.                                |
| fontStyle       | [FontStyle](ts-appendix-enums.md#fontstyle)                                  | No   | Yes   | Font style of the text, used to specify whether the text is displayed in italic. The options include Normal and Italic. For details, see [FontStyle](ts-appendix-enums.md#fontstyle). Default value: FontStyle.Normal.                                                                                  |
| fontFamily      | [Resource](ts-types.md#resource)&nbsp;\|&nbsp;string                                    | No   | Yes   | Font list, used to set the font used by the button text. You can pass a single font name string or multiple font names separated by commas (with priority from left to right, for example, 'Arial,HarmonyOS Sans'). The default font is 'HarmonyOS Sans'. You can [register a custom font](../js-apis-font.md). If this parameter is not passed, the default font is used.                                                            |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No  | Yes  | Background color of the button.                    |
| borderRadius    | [Length](ts-types.md#length) \| [BorderRadiuses](ts-types.md#borderradiuses9) | No   | Yes   | Corner radius, used to set the corner radius of the button. Unit: vp. Pass this parameter when you need to customize the corner radius style of the button; otherwise, the default corner radius is used.                                                                                                                                                           |
| primary         | boolean                                                                      | No   | Yes   | Controls whether the Enter key is responded to by this button by default after the dialog box is displayed. After the dialog box is displayed, if the Tab key is not used to switch focus, the button with **primary** set to **true** responds to the Enter key by default; if the Tab key is used to switch focus, the Enter key is responded to by the button that currently has focus. **true**: After the dialog box is displayed, if the Tab key is not used to switch focus, pressing the Enter key triggers the event bound to this button. **false**: After the dialog box is displayed, if the Tab key is not used to switch focus, pressing the Enter key does not trigger the event bound to this button. Default value: **false** |


## DateRange<sup>19+</sup>

Defines the date range, which specifies the start and end dates.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


| Name     | Type      | Read-Only     | Optional  | Description                           |
| ----------- | ---------- | ------| --------------------------------- | --------------------------------- |
| start | Date | No  | Yes  | Start date of the date range, which must not be later than the end date. The date range is invalid if this parameter is not passed in, the date format is invalid, the date is out of the supported range, or **start** is later than **end**. |
| end   | Date | No  | Yes  | End date of the date range. The date range is invalid if this parameter is not passed in, the date format is invalid, the date is out of the supported range, or **end** is earlier than **start**.          |


