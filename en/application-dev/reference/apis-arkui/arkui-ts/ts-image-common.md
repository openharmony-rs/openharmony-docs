# Image Analysis Types
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=07d05947a90cbd4c215e5174f7648fcf076bc9eb translatedAt=2026-08-28T01:38:00.737Z pushedAt=2026-09-01T03:22:26.145Z -->

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## PixelMap

type PixelMap = import('../api/@ohos.multimedia.image').default.PixelMap

Represents an image pixel map for reading or writing image data and accessing image information.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Type                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| import('../api/@ohos.multimedia.image').default.[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | Image pixel class, used to read or write image data and obtain image information. |

## ImageAnalyzerConfig<sup>12+</sup>

Provides image AI analyzer configuration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only| Optional| Description                  |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType](#imageanalyzertype12)[] | No | No | Image AI analysis type. |

## ImageAnalyzerType<sup>12+</sup>

Defines the image AI analysis type. If it is not set, subject recognition and text recognition are enabled by default.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value   | Description          |
| -------- | ----- | -------- |
| SUBJECT | 0  | Subject recognition.|
| TEXT | 1  | Text recognition.|
| OBJECT_LOOKUP | 2  | Object lookup.|

## ImageAIOptions<sup>12+</sup>

Provides the image AI analysis options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only| Optional| Description                  |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType](#imageanalyzertype12)[] | No | Yes | Image AI analysis type. |
| aiController | [ImageAnalyzerController](#imageanalyzercontroller12) | No| Yes| Image AI analysis controller.|

> **NOTE**
>
> The **types** parameter of this API has a higher priority than that of [ImageAnalyzerConfig](#imageanalyzerconfig12). This means that, if both parameters are set, the value set by this API takes precedence.
>
> This API depends on device capabilities and must be used together with the [enableAnalyzer](ts-basic-components-image.md#enableanalyzer11) API of the corresponding component (for example, the [Image](ts-basic-components-image.md) component).

## ImageAnalyzerController<sup>12+</sup>

Defines the image AI analysis controller. You can bind this object to a supported component and call the methods it provides through the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>12+</sup>

constructor()

A constructor used to create an **ImageAnalyzerController** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### getImageAnalyzerSupportTypes<sup>12+</sup>

getImageAnalyzerSupportTypes(): ImageAnalyzerType[]

Obtains the image AI analysis types supported by the component to which this controller is bound. Before calling this method, bind the controller to a component through the **aiController** attribute of components such as **Image** and **ImageAnimator**. Otherwise, an empty array is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| [ImageAnalyzerType](#imageanalyzertype12)[] | AI analysis type supported by the corresponding component. |

## ContentTransitionEffect<sup>21+</sup>

Defines the content transition effect.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 21.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional|Description|
| -------- | ---------- | -------- | -------- | -------- | 
| IDENTITY | [ContentTransitionEffect](#contenttransitioneffect21) | Yes| No| Applies no transition effect during content switching.|
| OPACITY | [ContentTransitionEffect](#contenttransitioneffect21) | Yes| No| Applies a fade-in/fade-out transition animation during content switching.|