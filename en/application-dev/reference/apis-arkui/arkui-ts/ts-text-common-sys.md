# Text Component Common APIs (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-09-01T11:47:06.250Z -->

Provides common control capabilities for text components such as TextInput, TextArea, and Search, including text content retrieval, keyboard appearance configuration, and content change reason tracking. It applies to scenarios where text input components need to be managed and controlled in a unified manner.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This page contains only the system APIs of this module. For details about other public APIs, see [Basic Type Definitions](ts-types.md) and [Common APIs of Text Components](ts-text-common.md).

## TextContentControllerBase

Represents the base controller for **TextInput**, **TextArea**, and **Search** components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### getText<sup>19+</sup>

getText(range?: TextRange): string

Obtains the text content within a specified range. This API can be used in the following scenarios:
- Obtain the text content selected by the user in a text editor for processing.
- Obtain the text content within a specific range for checking during content validation.
- Extract part of the text content for analysis or conversion in a text processing application.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | No   | Range of the text content to obtain, defined by start and end positions.<br>If the range is not specified, the entire text is obtained by default. If the start position is not specified, it defaults to index 0. If the end position is not specified, it defaults to the end of the text.|

**Return value**

| Type   | Description              |
| ------ | ---------------- |
| string | Returns the text content string in the specified range. When the specified start position is greater than the end position, an empty string is returned. |

## KeyboardGradientMode<sup>20+</sup>

Keyboard gradient blur effect.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                | Value| Description                                      |
| ---------------------------------- | --- | ---------------------------------------- |
| NONE | 0 | No gradient effect.|
| LINEAR_GRADIENT | 1 | Linear gradient blur effect of the keyboard settings from top to bottom, with the blur degree varying along the vertical direction. |

## KeyboardFluidLightMode<sup>20+</sup>

Enumerates keyboard fluid lighting effects.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                | Value| Description                                      |
| ---------------------------------- | --- | ---------------------------------------- |
| NONE | 0 | No fluid lighting effect.|
| BACKGROUND_FLUID_LIGHT | 1 | Fluid light effect for the keyboard settings background. |

## KeyboardAppearanceConfig<sup>20+</sup>

Describes the keyboard visual style configuration.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                                   | Read-Only| Optional| Description                                                   |
| ------- | ----------------------------------------------------------- | ---- | ---- | -------------------------------------------------------- |
| gradientMode  | [KeyboardGradientMode](#keyboardgradientmode20) | No   | Yes   | Gradient blur effect of the keyboard. Pass this parameter when a gradient blur effect needs to be set for the keyboard.<br>Default value: KeyboardGradientMode.NONE |
| fluidLightMode  | [KeyboardFluidLightMode](#keyboardfluidlightmode20) | No   | Yes   | Fluid light effect of the keyboard. Pass this parameter when a fluid light animation effect needs to be set for the keyboard.<br>Default value: KeyboardFluidLightMode.NONE (no fluid light effect) |

## TextChangeReason<sup>20+</sup>

Enumerates the reasons for component content changes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| ------- | ---- | ------------------- |
| UNKNOWN | 0 | Unknown reason.|
| INPUT | 1 | User input.|
| PASTE | 2 | Paste operation.|
| CUT | 3 | Cut operation.|
| DRAG | 4 | Drag and drop operation.|
| AUTO_FILL | 5 | Auto-fill operation.|
| AI_WRITE | 6 | AI-assisted writing.|
| REDO | 7 | Redo operation.|
| UNDO | 8 | Undo operation.|
| CONTROLLER | 9 | Component API call.|
| ACCESSIBILITY | 10 | Accessibility API.|
| COLLABORATION | 11 | Cross-device photo collaboration input. |
| STYLUS | 12 | Stylus input.|

## VoiceButtonOptions<sup>23+</sup>

Sets the voice button options.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name               | Type                                             | Read-Only| Optional| Description                                                                                 |
|--------------------|-------------------------------------------------|----|----|-------------------------------------------------------------------------------------|
| enabled              | boolean                                         | No  | Yes | Whether to enable or disable the voice button in the input box.<br>The value true means to enable the voice button, and false means to disable it.<br>Default value: false|