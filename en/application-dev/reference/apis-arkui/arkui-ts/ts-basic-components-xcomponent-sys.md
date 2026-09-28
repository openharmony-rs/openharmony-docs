# XComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-09-03T13:08:05.153Z pushedAt=2026-09-17T03:50:59.860Z -->

**XComponent** provides a surface for graphics rendering and media data input into your view. This component embeds the surface into the view, allowing you to customize the position and size of the surface. It is suitable for scenarios such as video playback, camera preview, and game rendering that require displaying self-rendered content within an application, making it convenient for you to flexibly control the display area and layering of the content.

> **NOTE**
>
> This component is supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [XComponent](ts-basic-components-xcomponent.md).

## XComponentOptions<sup>12+</sup>

Defines the options of the **XComponent**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| screenId<sup>17+</sup> | number | No | Yes |Associated screen ID of the component. With this parameter, the component can display the image of the associated screen. The screen ID can be obtained through the **getAllScreens** API of the [@ohos.screen](../js-apis-screen-sys.md#screengetallscreens) module. Default value: **0**, which indicates the primary screen. **System API:** This is a system API. |

  > **NOTE**
  >
  > This attribute is effective only when **type** is set to **SURFACE**.
  >
  > It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).

## APIs

### enableTransparentLayer<sup>18+</sup>

enableTransparentLayer(enabled: boolean)

Enables an independent layer for the **XComponent** component with a semi-transparent background color. That is, you can use this API to place the component content on a separate composition layer for rendering, so as to avoid rendering anomalies when the semi-transparent area is blended with the content below.

Using this API does not necessarily mean that an independent layer will be set. Due to some reasons such as hardware specifications (for example, lack of hardware support for independent layer compositing) and software specifications (for example, intersection between an independent layer and a UI component that has a blur effect), the semi-transparent **XComponent** may fail to be set as an independent layer.

To use this API effectively and avoid display issues, follow these guidelines:

1. If an **XComponent** with an independent layer overlaps with another **XComponent** below it, the **XComponent** below it should also be configured with an independent layer.

   ![Independent layer example](figures/Transparent_Layer_Example.png)

2. If UI components are placed below an **XComponent** that has an independent layer set through this API and a semi-transparent background, the displayed content of the UI components may disappear during composition.

   ![Independent layer display failure](figures/Transparent_Layer_Failure.png)

   An **XComponent** with an independent layer enabled must be placed below all UI elements that intersect with it.

   ![Independent layer correctly set](figures/Transparent_Layer_Correct_Example.png)

3. Set an independent layer for an **XComponent** with a semi-transparent background in static layout scenarios, for example, non-page transition scenarios and playback scenarios where video subtitles are static.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type    | Mandatory| Description                  |
| ------- | ------- | ---- | ---------------------- |
| enabled | boolean | Yes | Whether to enable an independent layer for the component with a semi-transparent background.<br>**true**: enable the independent layer; **false**: disable the independent layer.<br>When set to **true**, it may not take effect due to hardware specifications (for example, lack of hardware support for independent layer compositing) or software specifications (for example, intersection between an independent layer and a UI component that has a blur effect). For details, see the API description above.<br>Default value: **false** |

  > **NOTE**
  >
  > This attribute is effective only when **type** is set to **SURFACE**.
  >
  > It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).