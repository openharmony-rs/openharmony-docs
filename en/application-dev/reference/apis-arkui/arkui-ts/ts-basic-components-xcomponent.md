# XComponent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

**XComponent** provides a surface for graphics rendering and media data input into the view. This component embeds the surface into the view, allowing you to customize the position and size of the surface. It also supports AI image analysis, HDR video brightness adjustment, privacy protection against screen capture and recording, and canvas drawing. This component is suitable for scenarios that require high-performance rendering and media content display, such as video playback, camera preview, game rendering, and AI-based image recognition. For details, see [Custom Rendering (XComponent)](../../../ui/napi-xcomponent-guidelines.md).

> **NOTE**
>
> This component is supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Child Components
Not supported

## APIs

### XComponent<sup>19+</sup>

XComponent(params: NativeXComponentParameters)

Obtains an **XComponent** node instance on the native side, and registers the lifecycle callbacks for the surface held by the **XComponent** and the callbacks for component events, such as touch, mouse, and key events.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                               | Mandatory| Description                          |
| ------- | --------------------------------------- | ---- | ------------------------------ |
| params | [NativeXComponentParameters](#nativexcomponentparameters19) | Yes  | Configuration parameters of **XComponent**, which are used to obtain the **XComponent** node instance on the native side and register the lifecycle callbacks for the surface and the callbacks for component events.|

### XComponent<sup>12+</sup>

XComponent(options: XComponentOptions)

Creates an **XComponent** component, allowing you to obtain the **SurfaceId** value on the ArkTS side, register the lifecycle callbacks for the surface held by the **XComponent** and the callbacks for component events such as touch, mouse, and key events, and configure the AI analyzer feature.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                               | Mandatory| Description                          |
| ------- | --------------------------------------- | ---- | ------------------------------ |
| options | [XComponentOptions](#xcomponentoptions12) | Yes  | Configuration options of **XComponent**, which are used to obtain the surface ID and register surface lifecycle callbacks and component event callbacks on the ArkTS side, as well as configure the AI analysis feature.|

### XComponent<sup>10+</sup>

XComponent(value: {id: string, type: XComponentType, libraryname?: string, controller?: XComponentController})

Creates an **XComponent** component, whose lifecycle callbacks can be triggered from the native side.

This API is deprecated since API version 12. You are advised to use [XComponent(options: XComponentOptions)](#xcomponent12) instead.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                     | Mandatory| Description                                                        |
| ----------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| id          | string                                        | Yes  | Unique ID of the component. The value can contain a maximum of 128 characters. If the value exceeds 128 characters, it is invalid.                   |
| type        | [XComponentType](ts-appendix-enums.md#xcomponenttype10)   | Yes  | Type of the component.                                |
| libraryname | string                                        | No  | Name of the dynamic library compiled and output by the native layer of the application (the corresponding dynamic library does not support cross-module loading). This parameter is effective only when **type** is **SURFACE** or **TEXTURE**. If this parameter is not set, the dynamic library is not loaded.|
| controller  | [XComponentController](#xcomponentcontroller) | No  | Controller bound to the component, which can be used to invoke methods of the component (such as obtaining the surface ID and setting the surface display area). This parameter is valid only when **type** is **SURFACE** or **TEXTURE**. This parameter is passed when the **XComponent** behavior needs to be controlled on the ArkTS side. If this parameter is not passed, related component methods cannot be invoked through the controller.|

### XComponent<sup>(deprecated)</sup>

XComponent(value: {id: string, type: string, libraryname?: string, controller?: XComponentController})

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 12. You are advised to use [XComponent(value: {id: string, type: XComponentType, libraryname?: string, controller?: XComponentController})](#xcomponent10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                     | Mandatory| Description                                                        |
| ----------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| id          | string                                        | Yes  | Unique ID of the component. The value can contain a maximum of 128 characters. If the value exceeds 128 characters, it is invalid.                   |
| type        | string                                        | Yes  | Type of the **XComponent**. The options are as follows:<br>- **"surface"**: The custom content is displayed individually on the screen. This option is used for displaying EGL/OpenGL ES and media data.<br>- **"component"**<sup>9+</sup>: The component acts as a container where non-UI logic can be executed to dynamically load and display content.<br>Any other value is handled as **"surface"**.|
| libraryname | string                                        | No  | Name of the dynamic library compiled and output by the native layer of the application (the corresponding dynamic library does not support cross-module loading). This parameter takes effect only when **type** is **"surface"**. If this parameter is not set, the dynamic library is not loaded.|
| controller  | [XComponentController](#xcomponentcontroller) | No  | Controller bound to the component, which can be used to invoke methods of the component. This parameter takes effect only when the component type is **"surface"**. If this parameter is not set, no controller is bound.|

## XComponentOptions<sup>12+</sup>

Defines the options of the **XComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| type | [XComponentType](ts-appendix-enums.md#xcomponenttype10)         | No| No  | Type of the component.|
| controller | [XComponentController](#xcomponentcontroller) | No| No| Controller bound to the component, which can be used to invoke methods of the component. This parameter is effective only when **type** is **SURFACE** or **TEXTURE**.|
| imageAIOptions | [ImageAIOptions](ts-image-common.md#imageaioptions12) | No| Yes| AI analysis options for the component, which can be used to set the analysis type or bind an analysis controller. This parameter is effective only when **type** is **SURFACE** or **TEXTURE**. If this parameter is not set, no AI analysis option is configured. You can use the **enableAnalyzer** attribute to enable AI analysis separately.|

## NativeXComponentParameters<sup>19+</sup>

Defines the configuration parameters used by **XComponent** on the native side. The [FrameNode](../js-apis-arkui-frameNode.md) object corresponding to the **XComponent** created using the constructor parameter can be passed to the native side. You can use the NDK API to set the surface lifecycle and [add event listeners](../../../ui/ndk-add-component-events.md).

**Atomic service API**: This API can be used in atomic services since API version 19.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| type | [XComponentType](ts-appendix-enums.md#xcomponenttype10)         | No| No  | Type of the component.|
| imageAIOptions | [ImageAIOptions](ts-image-common.md#imageaioptions12) | No| Yes| AI analysis options for the component, which can be used to set the analysis type or bind an analysis controller. This parameter is effective only when **type** is **SURFACE** or **TEXTURE**. If this parameter is not set, no AI analysis option is configured. You can use the **enableAnalyzer** attribute to enable AI analysis separately.|

## Attributes
In addition to universal attributes, the following attributes are supported.
  > 
  > **NOTE**
  >
  > The **foregroundColor**, **obscured**, and **pixelStretchEffect** attributes are not supported. In API version 17 and earlier versions, when **type** is set to **SURFACE**, dynamic attribute setting, custom drawing, background setting (except **backgroundColor**), image effect (except **shadow**), **maskShape**, and **foregroundEffect** attributes are also not supported. Since API version 18, the following dynamic attributes are not supported for **type** set to **SURFACE**: **background**, **foregroundColor**, **animation**, **gesture**, **priorityGesture**, **parallelGesture**, **useEffect**, **renderGroup**, **flexGrow**, **direction**, **align**, **useSizeType**, **clip**, **geometryTransition**, **bindPopup**, **bindMenu**, **bindContextMenu**, **bindContentCover**, **bindSheet**, **stateStyles**, **restoreId**, **onVisibleAreaChange**, **accessibilityGroup**, **obscured**, **reuseId**, and **accessibilityVirtualNode**.
  >
  > For the **XComponent** component of the TEXTURE or SURFACE type, if the [renderFit](./ts-universal-attributes-renderfit.md#renderfit) attribute is not set, it defaults to **RenderFit.RESIZE_FILL**.
  > 
  > For the **XComponent** component of the **SURFACE** type, the background color is opaque black by default. In versions earlier than API version 18, the universal attribute [renderFit](./ts-universal-attributes-renderfit.md#renderfit18) of this component can only be set to **RenderFit.RESIZE_FILL**. Since API version 18, all enumerated values of **RenderFit** are supported.
  > 
  > For the **XComponent** component created using the [ArkUI NDK API](../../../ui/ndk-access-the-arkts-page.md), the [getAttribute](../capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute) function is not supported for obtaining the **renderFit** attribute value.
  
### enableAnalyzer<sup>12+</sup>

enableAnalyzer(enable: boolean)

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup.

This feature must be used together with [startImageAnalyzer](#startimageanalyzer12) and [stopImageAnalyzer](#stopimageanalyzer12) of **XComponentController**.

This attribute cannot be used together with the [overlay](ts-universal-attributes-overlay.md#overlay) attribute. If they are set at the same time, the [CustomBuilder](ts-types.md#custombuilder8) attribute in **overlay** has no effect. The AI analysis feature depends on device capabilities.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| enable | boolean | Yes| Whether to enable the AI image analyzer.<br>**true** to enable; **false** to disable.<br>Default value: **false**.|

  > **NOTE**
  >
  > This feature has effect only when **type** is set to **SURFACE** or **TEXTURE**.

### enableSecure<sup>13+</sup>

enableSecure(isSecure: boolean)

Sets whether to enable the secure surface to protect the content rendered within the component from being captured or recorded.

**Atomic service API**: This API can be used in atomic services since API version 13.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                  |
| -------- | ------- | ---- | ---------------------- |
| isSecure | boolean | Yes  | Whether to enable the secure surface.<br>The value **true** means to enable the secure surface, and **false** means the opposite.<br>Default value: **false**.|

  > **NOTE**
  >
  > This attribute is effective only when **type** is set to **SURFACE**.
  >
  > It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).

### hdrBrightness<sup>20+</sup>

hdrBrightness(brightness: number)

Sets the brightness of HDR video playback for the component.

> **NOTE**
>
> - This API takes effect only when **type** in **XComponent** constructor parameter is set to [XComponentType](ts-appendix-enums.md#xcomponenttype10).SURFACE; otherwise, it does not take effect.
>
> - It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type   | Mandatory| Description                  |
| -------- | ------- | ---- | ---------------------- |
| brightness | number | Yes  | Brightness of the HDR video.<br>Default value: **1.0**.<br>The value range is [0.0, 1.0]. Values below 0.0 are clamped to **0.0**, values above 1.0 are clamped to **1.0**, and all other invalid values default to **1.0**.<br>A value of **0.0** means the video is displayed at SDR brightness, while **1.0** represents the maximum permitted HDR brightness level.|

### hdrBrightness<sup>24+</sup>

hdrBrightness(brightness: number, type?: HdrType)

Adjusts the brightness of HDR content displayed by the component.<br>
If the **type** parameter is set to a value other than [HdrType](#hdrtype24).DEFAULT, check whether the **hdrFormats** attribute of [Display](../js-apis-display.md#display) contains the corresponding [HDRFormat](../../apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat) before calling this API.<br>The current device supports the corresponding HDR type and the parameter setting takes effect only when the value of **hdrFormats** contains the corresponding **HDRFormat**. Otherwise, the default value [HdrType](#hdrtype24).DEFAULT is used.<br>
The mapping is as follows.
   | Value of type| HDRFormat that hdrFormats Must Contain|
   | -------- | -------- |
   | [HdrType](#hdrtype24).AIHDR | [HDRFormat](../../apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat).VIDEO_AIHDR |

> **NOTE**
> 
> - This API takes effect only when **type** in **XComponent** constructor parameter is set to [XComponentType](ts-appendix-enums.md#xcomponenttype10).SURFACE; otherwise, it does not take effect.
>
> - It is not supported for **XComponent** components created using the [ArkUI NDK API](../../../ui/ndk-build-ui-overview.md).

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type   | Mandatory| Description                  |
| -------- | ------- | ---- | ---------------------- |
| brightness | number | Yes  | Brightness of HDR content.<br>Default value: **1.0**.<br>The value range is [0.0, 1.0]. Values below 0.0 are clamped to **0.0**, values above 1.0 are clamped to **1.0**, and all other invalid values default to **1.0**.<br>A value of **0.0** means the content is displayed at SDR brightness, while **1.0** represents the maximum permitted HDR brightness level.|
| type | [HdrType](#hdrtype24)| No  | HDR type when HDR content is displayed.<br>Default value: **HdrType.DEFAULT**|

## HdrType<sup>24+</sup>

Enumerates HDR rendering types for content.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name| Value| Description|
| ---- | -- | ---- |
| DEFAULT | 0 | Default HDR type, which uses the standard HDR rendering mode.<br>**Atomic service API**: This API can be used in atomic services since API version 24.|
| AIHDR | 1 | AI HDR type, which uses AI to intelligently extend dynamic range during non-HDR content rendering to achieve HDR visual effects.<br>**Atomic service API**: This API can be used in atomic services since API version 24.|
## Events

Since API version 12, the [universal events](ts-component-general-events.md) are supported when **type** is set to **SURFACE** or **TEXTURE**.

> **NOTE**
>
> When the **libraryname** parameter is set, [click events](ts-universal-events-click.md), [touch events](ts-universal-events-touch.md), [show/hide events](ts-universal-events-show-hide.md), [key events](ts-universal-events-key.md), [focus events](ts-universal-focus-event.md), and [mouse events](ts-universal-mouse-key.md) only respond to event APIs on the C API side.

The following events are effective only when **type** is set to **SURFACE** or **TEXTURE**.

### onLoad

onLoad(callback: OnNativeLoadCallback)

Triggered when the native loading is complete.

> **NOTE**
>
> This callback is triggered only when the **libraryname** parameter is set for **XComponent**. If the **libraryname** parameter is not set, use callbacks such as [onSurfaceCreated](#onsurfacecreated12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description                                      |
| ----- | ------ | ---- | ---------------------------------------- |
| callback | [OnNativeLoadCallback](#onnativeloadcallback18) | Yes   | Callback event triggered when the native loading is complete. This event is used to obtain the context of the **XComponent** instance.|

### onDestroy

onDestroy(event: VoidCallback)

Triggered when the native unloading is complete. The difference between **onDestroy** and [onSurfaceDestroyed](#onsurfacedestroyed12) is as follows: **onDestroy** is applicable to the scenario where the **libraryname** parameter is set, and the callback has no parameter. **onSurfaceDestroyed** is applicable to the scenario where the **libraryname** parameter is not set, and the callback parameter is **surfaceId**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description                                      |
| ----- | ------ | ---- | ---------------------------------------- |
| event | [VoidCallback](ts-types.md#voidcallback12) | Yes   | Callback event triggered when the native unloading is complete.|

## OnNativeLoadCallback<sup>18+</sup>

type OnNativeLoadCallback = (event?: object) =\> void

Triggered when the native loading of the **XComponent** is complete. This event is used to pass the context of the **XComponent** instance to you. The difference between this event and [onSurfaceCreated](#onsurfacecreated12) is as follows: The callback parameter of the **onLoad** event is the context object, which is applicable to the scenario where the **libraryname** parameter is set. The callback parameter of the **onSurfaceCreated** event is **surfaceId**, which is applicable to the scenario where the **libraryname** parameter is not set. The trigger time of the **onLoad** event is earlier than that of the **onSurfaceCreated** event.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description                                      |
| ----- | ------ | ---- | ---------------------------------------- |
| event | object | No   | Context of the **XComponent** object. The APIs contained in the context are defined at the native layer by developers. This parameter is passed when you need to use the methods defined at the native layer in the callback. If this parameter is not passed, the context object cannot be obtained in the callback.|

## XComponentController

Defines the controller of the **XComponent**. You can bind the controller to the **XComponent** to call the component APIs through the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

A constructor used to create a **XComponentController** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

  ```ts
  xComponentController: XComponentController = new XComponentController();
  ```

### getXComponentSurfaceId<sup>9+</sup>

getXComponentSurfaceId(): string

Obtains the ID of the surface held by the **XComponent**. This API works only when **type** of the **XComponent** is **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                     |
| ------ | ----------------------- |
| string | ID of the surface held by the **XComponent**.|

> **NOTE**
> 
> When you create an **XComponent** using a custom component node, the **onLoad** callback is triggered before the [onSurfaceCreated](#onsurfacecreated12) callback. This means that calling [getXComponentSurfaceId](#getxcomponentsurfaceid9) in the **onLoad** callback will not return a valid **surfaceId**. You are advised to obtain the **surfaceId** in the [onSurfaceCreated](#onsurfacecreated12) callback instead.

**Example**

```ts
// xxx.ets

@Entry
  @Component
  struct Index {
    myXComponentController: XComponentController = new XComponentController();

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        XComponent({
          type: XComponentType.SURFACE,
          controller: this.myXComponentController
        })
          .onLoad(() => {
            let surfaceId: string = this.myXComponentController.getXComponentSurfaceId();
            console.info("XComponent SurfaceId: " + surfaceId);
          })
      }
    }
  }
  ```

### setXComponentSurfaceSize<sup>(deprecated)</sup>

setXComponentSurfaceSize(value: {surfaceWidth: number, surfaceHeight: number}): void

Sets the width and height of the surface held by the **XComponent**. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. You are advised to use [setXComponentSurfaceRect](#setxcomponentsurfacerect12) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name          | Type  | Mandatory  | Description                     |
| ------------- | ------ | ---- | ----------------------- |
| surfaceWidth  | number | Yes   | Width of the surface held by the **XComponent**. The value must be greater than 0 and less than or equal to 8192, in px. If 0, a negative number, or any other invalid value is passed, the API does not take effect.|
| surfaceHeight | number | Yes   | Height of the surface held by the **XComponent**. The value must be greater than 0 and less than or equal to 8192, in px. If 0, a negative number, or any other invalid value is passed, the API does not take effect.|


### getXComponentContext

getXComponentContext(): Object

Obtains the context of an **XComponent** object. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| Object | Context of the **XComponent** object. The APIs contained in the context are defined by developers. The context is passed as the first parameter of the **onLoad** callback.|

### setXComponentSurfaceRect<sup>12+</sup>

setXComponentSurfaceRect(rect: SurfaceRect): void

Sets the display area for the surface held by the **XComponent**, including the width, height, and position coordinates relative to the top-left corner of the component. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                            | Mandatory| Description                             |
| ------ | ------------------------------------ | ---- | --------------------------------- |
| rect   | [SurfaceRect](#surfacerect12) | Yes  | Rectangle of the surface held by the **XComponent**.|

> **NOTE**
>
> If **offsetX** or **offsetY** in **rect** is not set or an abnormal value is passed, the offset effect of the surface display area relative to the x/y-axis of the **XComponent**'s upper-left corner defaults to center alignment.
>
> If **surfaceWidth** and **surfaceHeight** in the **rect** parameter are set to **0**, negative numbers, or other abnormal values, the display area set by calling this API does not take effect. If this API is not called to set the display area of the surface, **surfaceWidth** defaults to the component width, and **surfaceHeight** defaults to the component height.
>
> This API has a higher priority than attributes that can change the content offset and size, such as [border](ts-universal-attributes-border.md#border) and [padding](ts-universal-attributes-size.md#padding).

### getXComponentSurfaceRect<sup>12+</sup>

getXComponentSurfaceRect(): SurfaceRect

Obtains the display area for the surface held by the **XComponent**, including the width, height, and position coordinates relative to the top-left corner of the component. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                | Description                                 |
| ------------------------------------ | ------------------------------------- |
| [SurfaceRect](#surfacerect12) | Rectangle of the surface held by the **XComponent**.|

### onSurfaceCreated<sup>12+</sup>

onSurfaceCreated(surfaceId: string): void

Triggered when the surface held by the **XComponent** is created. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type| Mandatory| Description                                             |
| --------- | -------- | ---- | ------------------------------------------------- |
| surfaceId | string   | Yes  | ID of the surface held by the **XComponent**.|

> **NOTE**
>
> The callback is triggered only when the **libraryname** parameter is not set for the **XComponent**.

### onSurfaceChanged<sup>12+</sup>

onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void

Triggered when the size of the surface held by the **XComponent** changes, including the initial size change upon first creation. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                             | Mandatory| Description                                                   |
| --------- | ------------------------------------- | ---- | ------------------------------------------------------- |
| surfaceId | string                                | Yes  | ID of the surface held by the **XComponent**.      |
| rect      | [SurfaceRect](#surfacerect12) | Yes  | Area for displaying the surface held by the **XComponent**.|

> **NOTE**
>
> The callback is triggered only when the **libraryname** parameter is not set for the **XComponent**.

### onSurfaceDestroyed<sup>12+</sup>

onSurfaceDestroyed(surfaceId: string): void

Triggered when the surface held by the **XComponent** is destroyed. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**) or **TEXTURE**. For details, see [Creating an XComponent and Managing the Surface Lifecycle](../../../ui/napi-xcomponent-guidelines.md#creating-an-xcomponent-and-managing-the-surface-lifecycle).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type| Mandatory| Description                                             |
| --------- | -------- | ---- | ------------------------------------------------- |
| surfaceId | string   | Yes  | ID of the surface held by the **XComponent**.|

> **NOTE**
>
> The callback is triggered only when the **libraryname** parameter is not set for the **XComponent**.

### startImageAnalyzer<sup>12+</sup>

startImageAnalyzer(config: ImageAnalyzerConfig): Promise\<void>

Starts the AI image analyzer in the given settings. Before calling this API, make sure the AI image analyzer is enabled using [enableAnalyzer](#enableanalyzer12). This API is valid only when **type** of the **XComponent** is set to **SURFACE** or **TEXTURE**. This API uses a promise to return the result.<br>Because the image frame used for analysis is the one captured when this API is called, pay attention to the invoking time of this API.<br>If this API is repeatedly called before the execution is complete, an error callback is triggered.

> **NOTE**
> 
> The image analysis type cannot be dynamically modified.
> The AI analysis feature depends on device capabilities. If the device does not support this feature, an error code is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type     | Mandatory| Description                                                                  |
| ------ | --------- | ---- | ---------------------------------------------------------------------- |
| config   | [ImageAnalyzerConfig](ts-image-common.md#imageanalyzerconfig12) | Yes  | Settings of the AI image analyzer.|

**Return value**

| Type             | Description                                |
| ----------------- | ------------------------------------ |
| Promise\<void>  | Promise that returns no value. It is used to indicate AI-based analysis is successfully executed.|

**Error codes**

For details about the error codes, see [AI Image Analyzer Error Codes](errorcode-image-analyzer.md).

| ID| Error Message                                     |
| -------- | -------------------------------------------- |
| 110001 | Image analysis feature is unsupported.               |
| 110002 | Image analysis is currently being executed.  |
| 110003 | Image analysis is stopped.  |

### stopImageAnalyzer<sup>12+</sup>

stopImageAnalyzer(): void

Stops the AI image analyzer. This API is valid only when **type** of the XComponent is set to **SURFACE** or **TEXTURE**. You must call [enableAnalyzer](#enableanalyzer12) and [startImageAnalyzer](#startimageanalyzer12) to enable the AI analysis capability first. After this API is called, the content displayed as a result of the AI analysis will be destroyed.

> **NOTE**
> 
> If this API is called when the **startImageAnalyzer** API has not yet returned any result, an error callback is triggered.
> This feature depends on device capabilities.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### setXComponentSurfaceRotation<sup>12+</sup>

setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void

Sets whether to lock the orientation of the surface held by this **XComponent** when the screen rotates. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                            | Mandatory| Description                             |
| ------ | ------------------------------------ | ---- | --------------------------------- |
| rotationOptions   | [SurfaceRotationOptions](#surfacerotationoptions12) | Yes| Whether to lock the orientation of the surface held by the current **XComponent** when the screen rotates.|

> **NOTE**
>
> If **rotationOptions** is not set, the surface held by this **XComponent** rotates with the screen by default.
>
> The orientation lock is only applied during the rotation process and is released once the rotation is complete.
>
> The setting takes effect only when the screen is rotated by 90°, that is, when it switches between landscape and portrait modes.
>
> Make sure the width and height of **Buffer** remain unchanged after locking the orientation to prevent distortion.

### getXComponentSurfaceRotation<sup>12+</sup>

getXComponentSurfaceRotation(): Required\<SurfaceRotationOptions>

Obtains whether the orientation of the surface held by this **XComponent** is locked when the screen rotates. This API works only when **type** of the **XComponent** is set to **SURFACE** (**"surface"**).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                | Description                                 |
| ------------------------------------ | ------------------------------------- |
| Required<[SurfaceRotationOptions](#surfacerotationoptions12)> | Whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates.|

### lockCanvas<sup>20+</sup>

lockCanvas(): DrawingCanvas | null

Obtains a canvas object for drawing content on the **XComponent** component. For details about the drawing methods, see [Canvas](../../apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**
| Type                                | Description                                 |
| ------------------------------------ | ------------------------------------- |
| [DrawingCanvas](ts-drawingrenderingcontext.md#drawingcanvas) \| null | Canvas object that can be used to render on the XComponent component. If the canvas object cannot be obtained (for example, the surface has not been created or the canvas is occupied and not released), **null** is returned.|

> **NOTE**
>
> This API returns **null** if the canvas object cannot be obtained due to the current state of the **XComponent** component. The possible causes are as follows:
>
> 1. The surface held by the **XComponent** has not been created yet (you can determine this by setting the [onLoad](#onload) or [onSurfaceCreated](#onsurfacecreated12) callback, which is triggered after the surface is created).
>
> 2. A previous canvas object obtained using **lockCanvas()** has not been released with [unlockCanvasAndPost](#unlockcanvasandpost20).
>
> This API is only effective when the **XComponent** type is **TEXTURE** or **SURFACE**.
>
> After using this API, do not simultaneously obtain the **NativeWindow** instance on the NDK side and call NDK rendering APIs. Doing so may cause buffer contention and context to occur, leading to rendering exceptions such as visual artifacts.
>
> This API must be used in conjunction with [unlockCanvasAndPost](#unlockcanvasandpost20). For the implementation example, see [Example 3: Drawing Content on the XComponent Using a Canvas Object](#example-3-drawing-content-on-the-xcomponent-using-a-canvas-object).

### unlockCanvasAndPost<sup>20+</sup>

unlockCanvasAndPost(canvas: DrawingCanvas): void

Submits the drawn content from a canvas object to the display area of the **XComponent** component and releases the canvas object.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| canvas | [DrawingCanvas](ts-drawingrenderingcontext.md#drawingcanvas)| Yes| Canvas object previously obtained using **lockCanvas()**.|

> **NOTE**
>
> 1. Once released using **unlockCanvasAndPost()**, a canvas object becomes immediately unusable.
>
> 2. This API is only effective when the **XComponent** type is **TEXTURE** or **SURFACE**.
>
> 3. After using this API, do not simultaneously obtain the **NativeWindow** instance on the NDK side and call related APIs for rendering. Doing so may cause buffer contention and context to occur, leading to rendering exceptions such as visual artifacts.
>
> 4. This API must be used in conjunction with [lockCanvas](#lockcanvas20). For the implementation example, see [Example 3: Drawing Content on the XComponent Using a Canvas Object](#example-3-drawing-content-on-the-xcomponent-using-a-canvas-object).

### setXComponentSurfaceConfig<sup>22+</sup>

setXComponentSurfaceConfig(config: SurfaceConfig): void

Sets the options of the surface created by the **XComponent**, which determine whether the surface held by the **XComponent** is considered opaque during rendering. When the content rendered on the surface is completely opaque, you can set the surface to opaque to improve rendering performance. When the rendered content contains transparent areas, you need to keep the surface non-opaque to ensure that the transparency effect is correctly displayed.

> **NOTE**
>
> This API takes effect only when the type of **XComponent** is **TEXTURE** or **SURFACE**.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| config | [SurfaceConfig](#surfaceconfig22)| Yes| Surface configuration, which is used to set whether the surface held by the **XComponent** needs to be treated as opaque during rendering.|

## SurfaceRotationOptions<sup>12+</sup>

Defines whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type  | Read-Only| Optional| Description                                                        |
| ------------- | ------ | ------ | ---- | ------------------------------------------------------------ |
| lock       | boolean | No| Yes  | Whether the orientation of the surface is locked when the screen rotates. If this parameter is not set, the default value **false** is used, indicating that the orientation is not locked.<br>**true**: The orientation of the surface is locked when the screen rotates. **false**: The orientation of the surface is not locked when the screen rotates.|

## SurfaceRect<sup>12+</sup>

Describes the rectangle of the surface held by the **XComponent**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type  | Read-Only| Optional| Description                                                        |
| ------------- | ------ | ------ | ---- | ------------------------------------------------------------ |
| offsetX       | number | No  | Yes  | X-coordinate of the surface rectangle relative to the upper-left corner of the **XComponent**.<br>Unit: px If this parameter is not set, the surface is displayed in the center by default.|
| offsetY       | number | No  | Yes  | Y-coordinate of the surface rectangle relative to the upper left corner of the **XComponent**.<br>Unit: px If this parameter is not set, the surface is displayed in the center by default.|
| surfaceWidth  | number | No  | No  | Width of the surface rectangle.<br>Unit: px.                           |
| surfaceHeight | number | No  | No  | Height of the surface rectangle.<br>Unit: px.                           |

> **NOTE**
>
> If neither [setXComponentSurfaceRect](#setxcomponentsurfacerect12) is called nor attributes such as [border](ts-universal-attributes-border.md#border) and [padding](ts-universal-attributes-size.md#padding) are set, the values of **surfaceWidth** and **surfaceHeight** are the size of the **XComponent**.
> 
> Make sure the values of **surfaceWidth** and **surfaceHeight** do not exceed 8192 px. Exceeding this limit may lead to rendering issues.
>
> In immersive scenarios, **SurfaceRect** of the default layout does not include the safe area. You need to call the [setXComponentSurfaceRect](#setxcomponentsurfacerect12) API to set the surface display area to achieve the immersive effect.

## SurfaceConfig<sup>22+</sup>

Describes whether the surface held by the **XComponent** is treated as opaque during rendering.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type  | Read-Only| Optional| Description                                                        |
| ------------- | ------ | ------ | ---- | ------------------------------------------------------------ |
| isOpaque       | boolean | No| Yes  | Whether the surface held by the **XComponent** is treated as opaque during rendering. If this attribute is not set, the default value **false** is used, indicating that the transparency of the pixels in the content drawn on the surface will be applied during rendering.<br>**true**: yes; **false**: no<br>Default value: **false**.|

## Example

You can preview how this component looks on a real device, but not in DevEco Studio Previewer.


### Example 1: Enabling AI Image Analyzer

This example shows how to use the **enableAnalyzer** attribute to enable the AI image analyzer. You can use **XComponentController** to start or stop the AI image analyzer.

<!--RP1-->
> **NOTE**
>
> For details about how to implement the rendering logic (functions related to **nativeRender**), see [ArkTS XComponent Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).
<!--RP1End-->

```ts
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import nativeRender from 'libnativerender.so'; // Custom own .so file implementation (see the preceding note for details).

class CustomXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
    nativeRender.SetSurfaceId(BigInt(surfaceId));
  }

  onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
    console.info(`onSurfaceChanged surfaceId: ${surfaceId}, rect: ${JSON.stringify(rect)}`);
    nativeRender.ChangeSurface(BigInt(surfaceId), rect.surfaceWidth, rect.surfaceHeight);
  }

  onSurfaceDestroyed(surfaceId: string): void {
    console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    nativeRender.DestroySurface(BigInt(surfaceId));
  }
}

@Entry
@Component
struct XComponentExample {
  xComponentController: XComponentController = new CustomXComponentController();
  private config: ImageAnalyzerConfig = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT]
  };
  private aiController: ImageAnalyzerController = new ImageAnalyzerController();
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  };
  @State xcWidth: string = "720px";
  @State xcHeight: string = "720px";
  @State currentStatus: string = "index";

  build() {
    Column({ space: 5 }) {
      Row() {
        Text('Native XComponent Sample')
          .fontSize('24fp')
          .fontWeight(500)
          .margin({
            left: 24,
            top: 12
          })
      }
      .margin({ top: 24 })
      .width('100%')
      .height(56)

      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController,
        imageAIOptions: this.options
      })
        .width(this.xcWidth)
        .height(this.xcHeight)
        .enableAnalyzer(true)
        .onClick(() => {
          let surfaceId = this.xComponentController.getXComponentSurfaceId();
          nativeRender.ChangeColor(BigInt(surfaceId));
          let hasChangeColor: boolean = false;
          let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
          if (status) {
            hasChangeColor = status.hasChangeColor;
          }
          if (hasChangeColor) {
            this.currentStatus = "change color";
          }
        })
      Text(this.currentStatus)
        .fontSize('24fp')
        .fontWeight(500)
      Column() {
        Button('start AI analyze')
          .onClick(() => {
            this.xComponentController.startImageAnalyzer(this.config)
              .then(() => {
                console.info("analysis complete");
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to start image analyzer. Code: ${error.code}, message: ${error.message}`);
              })
          })
          .margin(2)
        Button('stop AI analyze')
          .onClick(() => {
            this.xComponentController.stopImageAnalyzer();
          })
          .margin(2)
        Button('get analyzer types')
          .onClick(() => {
            this.aiController.getImageAnalyzerSupportTypes();
          })
          .margin(2)
        Button('Draw Star')
          .fontSize('16fp')
          .fontWeight(500)
          .onClick(() => {
            let surfaceId = this.xComponentController.getXComponentSurfaceId();
            console.info(`surface rect is ${this.xComponentController.getXComponentSurfaceRect()}`);
            nativeRender.DrawPattern(BigInt(surfaceId));
            let hasDraw: boolean = false;
            let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
            if (status) {
              hasDraw = status.hasDraw;
            }
            if (hasDraw) {
              this.currentStatus = "draw star";
            }
          })
          .margin(2)
      }.justifyContent(FlexAlign.Center)
    }
    .width('100%')
  }
}
```
![AIXComponent](./figures/AIXComponent.gif)


### Example 2: Locking the Surface Orientation During Screen Rotation

This example shows how to use **setXComponentSurfaceRotation** to lock the surface orientation during screen rotation so that the surface does not rotate with the screen.

> **NOTE**
>
> For details about how to implement the rendering logic (functions related to **nativeRender**), see <!--RP2-->[ArkTS XComponent Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).<!--RP2End-->

```ts
// xxx.ets
import nativeRender from 'libnativerender.so';

class MyXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
    nativeRender.SetSurfaceId(BigInt(surfaceId));
  }

  onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
    console.info(`onSurfaceChanged surfaceId: ${surfaceId}, rect: ${JSON.stringify(rect)}`);
    nativeRender.ChangeSurface(BigInt(surfaceId), rect.surfaceWidth, rect.surfaceHeight);
  }

  onSurfaceDestroyed(surfaceId: string): void {
    console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    nativeRender.DestroySurface(BigInt(surfaceId));
  }
}

@Entry
@Component
struct Index {
  @State isLock: boolean = true;
  @State xcWidth: number = 500;
  @State xcHeight: number = 700;
  myXComponentController: XComponentController = new MyXComponentController();

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Start }) {
      XComponent({
        id: "XComponent",
        type: XComponentType.SURFACE,
        controller: this.myXComponentController
      })
        .onLoad(() => {
          let surfaceRotation: SurfaceRotationOptions = { lock: this.isLock };
          this.myXComponentController.setXComponentSurfaceRotation(surfaceRotation);
          console.info("Surface getXComponentSurfaceRotation lock = " +
          this.myXComponentController.getXComponentSurfaceRotation().lock);
        })
        .width(this.xcWidth)
        .height(this.xcHeight)
      Button("Draw")
        .onClick(() => {
          let surfaceId = this.myXComponentController.getXComponentSurfaceId();
          nativeRender.DrawPattern(BigInt(surfaceId));
        })
    }
  }
}
```

### Example 3: Drawing Content on the XComponent Using a Canvas Object

From API version 20, this example demonstrates how to return a canvas object by calling [lockCanvas](#lockcanvas20), call the corresponding drawing API via the canvas object, and then call [unlockCanvasAndPost](#unlockcanvasandpost20) to draw content on the **XComponent**.

```ts
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  private xcController: XComponentController = new XComponentController();
  private mCanvas: DrawingCanvas | null = null;

  build() {
    Column() {
      XComponent({ type: XComponentType.SURFACE, controller: this.xcController })
        .width("80%")
        .height("80%")
        .onLoad(() => {
          this.mCanvas = this.xcController.lockCanvas();
          if (this.mCanvas) {
            this.mCanvas.drawColor(255, 240, 250, 255); // Before each drawing operation, the entire XComponent area must be fully redrawn. This API can be used to achieve this.
            const brush = new drawing.Brush(); // Create a brush object.
            brush.setColor({ // Set the color of the brush.
              alpha: 255,
              red: 39,
              green: 135,
              blue: 217
            });
            this.mCanvas.attachBrush(brush); // Attach the brush to the canvas.
            this.mCanvas.drawRect({ // Draw a rectangle.
              left: 300,
              right: 800,
              top: 100,
              bottom: 800
            });
            this.mCanvas.detachBrush(); // Detach the brush from the canvas.
            this.xcController.unlockCanvasAndPost(this.mCanvas);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
![DrawingCanvas Example](./figures/DrawingCanvas.PNG)

### Example 4: Implementing an Immersive Effect

From API version 20, building upon Example 3, the **setXComponentSurfaceRect** API is called to set the surface area to achieve an immersive effect.

```ts
// xxx.ets
import { display } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  private xcController: XComponentController = new XComponentController();
  private mCanvas: DrawingCanvas | null = null;
  @State screenWidth: number = 0;
  @State screenHeight:number = 0;
  aboutToAppear() {
    try {
      const displayClass = display.getDefaultDisplaySync();
      this.screenWidth = displayClass.width;
      this.screenHeight = displayClass.height;
    } catch (error) {
      console.error(`Failed to get default display. Code: ${error.code}, message: ${error.message}`);
    }
  }

  build() {
    Column() {
      XComponent({ type: XComponentType.SURFACE, controller: this.xcController })
        .width('100%')
        .height('100%')
        .onLoad(() => {
          // Set the surface size. If the size is too large, the drawing time may be long.
          this.xcController.setXComponentSurfaceRect({surfaceWidth: this.screenWidth, surfaceHeight: this.screenHeight, offsetX: 0, offsetY: 0});
          this.mCanvas = this.xcController.lockCanvas();
          if (this.mCanvas) {
            this.mCanvas.drawColor(255, 39, 135, 217); // Before each drawing operation, the entire XComponent area must be fully redrawn. This API can be used to achieve this.
            this.xcController.unlockCanvasAndPost(this.mCanvas);
          }
        })
        .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]);
    }
    .height('100%')
    .width('100%')
  }
}
```
![Example of setXComponentSurfaceRect](./figures/setXComponentSurfaceRect04.jpeg)

### Example 5: Setting Whether the Surface Held by XComponent Needs to Be Treated as Opaque During Rendering

In API version 22 and later versions, this example calls the [setXComponentSurfaceConfig](#setxcomponentsurfaceconfig22) API to set whether the surface held by the **XComponent** is treated as opaque during rendering.

> **NOTE**
>
> For details about how to implement the rendering logic (functions related to **nativeRender**), see <!--RP2-->[ArkTS XComponent Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkTSXComponent).<!--RP2End-->

```ts
// xxx.ets
import nativeRender from 'libnativerender.so'; // Custom own .so file implementation (see the preceding note for details).

// Override XComponentController to set lifecycle callbacks.
class MyXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
    nativeRender.SetSurfaceId(BigInt(surfaceId));
  }
  onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
    console.info(`onSurfaceChanged surfaceId: ${surfaceId}, rect: ${JSON.stringify(rect)}`);
    // Call ChangeSurface to draw content in onSurfaceChanged.
    nativeRender.ChangeSurface(BigInt(surfaceId), rect.surfaceWidth, rect.surfaceHeight);
  }
  onSurfaceDestroyed(surfaceId: string): void {
    console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    nativeRender.DestroySurface(BigInt(surfaceId));
  }
}

@Entry
@Component
struct Index {
  @State currentStatus: string = "index";
  xComponentController: XComponentController = new MyXComponentController();

  aboutToAppear(): void {
    //Set the surface held by XComponent to be opaque during rendering.
    this.xComponentController.setXComponentSurfaceConfig({ isOpaque: true });
  }

  build() {
    Column() {
      Column({ space: 10 }) {
        XComponent({
          type: XComponentType.SURFACE,
          controller: this.xComponentController
        })
          .backgroundColor(Color.Transparent)
        Text(this.currentStatus)
          .fontSize('24fp')
          .fontWeight(500)
      }
      .onClick(() => {
        let surfaceId = this.xComponentController.getXComponentSurfaceId();
        nativeRender.ChangeColor(BigInt(surfaceId));
        let hasChangeColor: boolean = false;
        let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
        if (status) {
          hasChangeColor = status.hasChangeColor;
        }
        if (hasChangeColor) {
          this.currentStatus = "change color";
        }
      })
      .margin({
        top: 27,
        left: 12,
        right: 12
      })
      .height('40%')
      .width('90%')
      Row() {
        Button('Draw Star')
          .fontSize('16fp')
          .fontWeight(500)
          .margin({ bottom: 24 })
          .onClick(() => {
            let surfaceId = this.xComponentController.getXComponentSurfaceId();
            nativeRender.DrawPattern(BigInt(surfaceId));
            let hasDraw: boolean = false;
            let status = nativeRender.GetXComponentStatus(BigInt(surfaceId));
            if (status) {
              hasDraw = status.hasDraw;
            }
            if (hasDraw) {
              this.currentStatus = "draw star";
            }
          })
          .width('53.6%')
          .height(40)
      }
      .width('100%')
      .justifyContent(FlexAlign.Center)
      .alignItems(VerticalAlign.Bottom)
      .layoutWeight(1)
    }
    .width('100%')
    .height('100%')
  }
}
```

![Example of setXComponentSurfaceConfig](./figures/surfaceConfig.jpeg)
