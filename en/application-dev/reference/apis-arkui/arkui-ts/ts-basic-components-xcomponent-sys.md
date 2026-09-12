# XComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-09-03T13:08:05.153Z -->

Provides a surface for graphics rendering and media data input. **XComponent** embeds the surface into the view, allowing you to customize the position and size of the surface. It is suitable for scenarios such as video playback, camera preview, and game rendering that require displaying self-rendered content within an application, making it convenient for developers to flexibly control the display area and layering of the content.

> **NOTE**
>
> This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs of this module. For details about other public APIs, see [XComponent](ts-basic-components-xcomponent.md).

## XComponentOptions<sup>12+</sup>

Defines the options of the **XComponent**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| screenId<sup>17+</sup> | number | No | Yes | Sets the ID of the screen associated with the component. With this parameter, the screen content associated with the component can be displayed on the component. The screen ID can be obtained through the getAllScreens API of the [@ohos.screen](../js-apis-screen-sys.md#screengetallscreens) module. Default value: **0**, which indicates the primary screen. **System API:** This is a system API. |

  > **NOTE**
  >
  > This attribute is effective only when **type** is set to **SURFACE**.
  >
  > It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).

## APIs

### enableTransparentLayer<sup>18+</sup>

enableTransparentLayer(enabled: boolean)

Use this API when an **XComponent** with a semi-transparent background color needs to enable an independent layer (that is, to place the component content on a separate composition layer for rendering, so as to avoid rendering anomalies when the semi-transparent area is blended with the content below).

Using this API does not necessarily mean that an independent layer will be set. Due to the following reasons, such as hardware specifications (for example, lack of hardware support for independent layer hardware composition) and software specifications (for example, an independent layer intersecting with a UI component that has a blur effect), a semi-transparent **XComponent** may fail to be set as an independent layer.

To use this API effectively and avoid display issues, follow these guidelines:

1. If an **XComponent** with an independent layer overlaps with another **XComponent** below it, the **XComponent** below it should also be configured with an independent layer.

   ![Independent layer example](figures/Transparent_Layer_Example.png)

2. If UI components are placed below an **XComponent** that has an independent layer set through this API and a semi-transparent background, the displayed content of the UI components will disappear during composition.

   ![Independent layer display failure](figures/Transparent_Layer_Failure.png)

   An **XComponent** with an independent layer enabled must be placed below all UI elements that intersect with it.

   ![Independent layer correctly set](figures/Transparent_Layer_Correct_Example.png)

3. Set an independent layer for an XComponent with a semi-transparent background in static layout scenarios, for example, non-page transition scenarios and playback scenarios where video subtitles are static.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type    | Mandatory| Description                  |
| ------- | ------- | ---- | ---------------------- |
| enabled | boolean | Yes | Whether to enable the independent layer of the component in the semi-transparent background state.<br>true: enables the independent layer; false: disables the independent layer.<br>When set to true, it may not take effect due to hardware specifications (for example, the hardware does not support hardware composition of the independent layer) or software specifications (for example, the independent layer intersects with a UI component with a blur effect). For details, see the API description above.<br>Default value: false |

  > **NOTE**
  >
  > This attribute is effective only when **type** is set to **SURFACE**.
  >
  > It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).