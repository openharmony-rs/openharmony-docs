# Image Analysis Types
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## PixelMap

type PixelMap = PixelMap

Represents an image pixel map for reading or writing image data and accessing image information.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Type                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md) | Image pixel map class for reading or writing image data and accessing image information.|

## ImageAnalyzerConfig<sup>12+</sup>

Provides AI image analyzer configuration.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only| Optional| Description                  |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType[]](#imageanalyzertype12) | No| No| AI image analysis types.|

## ImageAnalyzerType<sup>12+</sup>

Defines the AI image analysis type. If it is not set, subject recognition and text recognition are enabled by default.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value   | Description          |
| -------- | ----- | -------- |
| SUBJECT | 0  | Subject recognition.|
| TEXT | -  | Text recognition.|
| OBJECT_LOOKUP | -  | Object lookup.|

## ImageAIOptions<sup>12+</sup>

Provides the AI image analysis options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type               | Read-Only| Optional| Description                  |
| ------ | ----------------- | ---- | -------------------- | -------------------- |
| types | [ImageAnalyzerType[]](#imageanalyzertype12) | No| Yes| AI image analysis types.|
| aiController | [ImageAnalyzerController](#imageanalyzercontroller12) | No| Yes| AI image analysis controller.|

> **NOTE**
>
> The **types** parameter of this API has a higher priority than that of [ImageAnalyzerConfig](#imageanalyzerconfig12). This means that, if both parameters are set, the value set by this API takes precedence.
>
> This API depends on device capabilities and must be used together with the **enableAnalyzer** API of the corresponding component (for example, the [Image](ts-basic-components-image.md#enableanalyzer11) component).

## ImageAnalyzerController<sup>12+</sup>

Implements an AI image analysis controller, which provides control for image analysis features when bound to supported components.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>12+</sup>

constructor()

A constructor used to create an **ImageAnalyzerController** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### getImageAnalyzerSupportTypes<sup>12+</sup>

getImageAnalyzerSupportTypes(): ImageAnalyzerType[]

Obtains the analysis types supported by the corresponding component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| [ImageAnalyzerType[]](#imageanalyzertype12) | Analysis type supported by the corresponding component.|

## ContentTransitionEffect<sup>21+</sup>

Defines the content transition effect.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### IDENTITY<sup>21+</sup>

static get IDENTITY(): ContentTransitionEffect

Applies no transition effect during content switching.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                                           |
| ------------------------------------------ | ----------------------------------------------- |
| [ContentTransitionEffect](#contenttransitioneffect21)   | Content transition effect. |

### OPACITY<sup>21+</sup>

static get OPACITY(): ContentTransitionEffect

Applies a fade-in/fade-out transition animation during content switching.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                                           |
| ------------------------------------------ | ----------------------------------------------- |
| [ContentTransitionEffect](#contenttransitioneffect21)   | Content transition effect. |
