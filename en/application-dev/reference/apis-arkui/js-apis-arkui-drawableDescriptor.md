# @ohos.arkui.drawableDescriptor (DrawableDescriptor)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

This module provides capabilities for layered icon composition (foreground, background, mask), animated image control, and basic image processing.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

## Modules to Import

```ts
import {
  DrawableDescriptor,
  LayeredDrawableDescriptor,
  AnimatedDrawableDescriptor,
  AnimationOptions,
  AnimationController
} from '@kit.ArkUI';
```
## DrawableDescriptorLoadedResult<sup>21+</sup>

Represents the result of loading an image resource or URI.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type   | Read-Only| Optional | Description             |
| ---------- | ------ | -----| ----|------------------------ |
| imageWidth   | number | No| No| Image width.<br>Unit: px.|
| imageHeight | number | No| No| Image height.<br>Unit: px.|

**Example**

```ts
import { AnimatedDrawableDescriptor, DrawableDescriptor, DrawableDescriptorLoadedResult } from '@kit.ArkUI';

let options: AnimationOptions = { duration: 2000, iterations: 1 };
let drawable: DrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options)
try {
    // You can preload animated image resources into the memory.
    let result: DrawableDescriptorLoadedResult = this.drawable.loadSync()
    console.info(`load result = ${JSON.stringify(result)}`)
} catch(e) {
    console.error("load failed")
}
```
## DrawableDescriptor

Represents the base class providing overridable methods for [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) acquisition and image resource loading.

### getPixelMap

getPixelMap(): image.PixelMap

Obtains this **pixelMap** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description      |
| ---------------------------------------- | -------- |
| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | **PixelMap** object.|

**Example**

  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI'
import { image } from '@kit.ImageKit'
let resManager = this.getUIContext().getHostContext()?.resourceManager;
// Replace $r('app.media.app_icon') with the image resource file you use.
let pixmap: DrawableDescriptor = (resManager?.getDrawableDescriptor($r('app.media.icon')
    .id)) as DrawableDescriptor; // When the passed resource ID or name is a regular image, a DrawableDescriptor object is generated.
let pixmapNew: image.PixelMap | undefined = pixmap?.getPixelMap();
  ```

### loadSync<sup>21+</sup>

loadSync(): DrawableDescriptorLoadedResult

Synchronously loads the image resource and returns the loading result.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| [DrawableDescriptorLoadedResult](#drawabledescriptorloadedresult21) | Image resource loading result.|

**Error codes**

For details about the error codes, see [DrawableDescriptor Error Codes](errorcode-drawable-descriptor.md).

| ID| Error Message    |
| -------- | ------------ |
| 111001   | resource loading failed. |

```ts
import { AnimatedDrawableDescriptor, DrawableDescriptor, DrawableDescriptorLoadedResult, AnimationOptions } from '@kit.ArkUI';

let options: AnimationOptions = { duration: 2000, iterations: 1 };
let drawable: DrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), options)
try {
    // You can preload animated image resources into the memory.
    let result: DrawableDescriptorLoadedResult = drawable.loadSync()
    console.info(`load result = ${JSON.stringify(result)}`)
} catch(e) {
    console.error("load failed")
}
```

### load<sup>21+</sup>

load(): Promise\<DrawableDescriptorLoadedResult>

Asynchronously loads the image resource and returns the loading result. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| [Promise\<DrawableDescriptorLoadedResult>](#drawabledescriptorloadedresult21) | Image resource loading result.|

**Error codes**

For details about the error codes, see [DrawableDescriptor Error Codes](errorcode-drawable-descriptor.md).

| ID| Error Message    |
| -------- | ------------ |
| 111001   | resource loading failed. |

```ts
import {
  AnimatedDrawableDescriptor,
  DrawableDescriptor,
  DrawableDescriptorLoadedResult,
  AnimationOptions
} from '@kit.ArkUI';

let options: AnimationOptions = { duration: 2000, iterations: 1 };
let drawable: DrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), options)
drawable.load().then((result: DrawableDescriptorLoadedResult) => {
  console.info(`load result = ${JSON.stringify(result)}`)
}).catch(() => {
  console.info(`load failed`)
})
```

## PixelMapDrawableDescriptor<sup>12+</sup>

Implements a **PixelMapDrawableDescriptor** object , which can be created by passing in a **pixelMap** object. Inherits from [DrawableDescriptor](#drawabledescriptor).

### constructor<sup>12+</sup>

constructor(src?: image.PixelMap)

A constructor used to create a **PixelMapDrawableDescriptor** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type             | Mandatory | Description                                      |
| --------- | ---------------- | ---- | ------------------------------------------ |
| src | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | No| **PixelMap** image data.|

## LayeredDrawableDescriptor

Creates a **LayeredDrawableDescriptor** object when the passed resource ID or name belongs to a JSON file that contains foreground and background resources. Inherits from [DrawableDescriptor](#drawabledescriptor).

The **drawable.json** file is located under **entry/src/main/resources/base/media** in the project directory. Below shows the file content:

```json
{
  "layered-image":
  {
    "background" : "$media:background",
    "foreground" : "$media:foreground"
  }
}
```

**Example**

This example creates a **LayeredDrawableDescriptor** object using a JSON file.

```ts
// xxx.ets
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private resManager = this.getUIContext().getHostContext()?.resourceManager;
  // Replace $r('app.media.drawable') with the image resource file you use.
  private layeredDrawableDescriptor: DrawableDescriptor | undefined =
    this.resManager?.getDrawableDescriptor($r('app.media.drawable').id);

  build() {
    Row() {
      Column() {
        Image((this.layeredDrawableDescriptor instanceof LayeredDrawableDescriptor) ?
          this.layeredDrawableDescriptor : undefined)
        Image((this.layeredDrawableDescriptor instanceof LayeredDrawableDescriptor) ?
          this.layeredDrawableDescriptor?.getForeground()?.getPixelMap() : undefined)
      }.height('50%')
    }.width('50%')
  }
}
```

This example creates a **LayeredDrawableDescriptor** object using a **PixelMapDrawableDescriptor** object.

```ts
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct Index {
  @State fore1: image.PixelMap | undefined = undefined;
  @State back1: image.PixelMap | undefined = undefined;

  @State foregroundDraw: DrawableDescriptor | undefined = undefined;
  @State backgroundDraw: DrawableDescriptor | undefined = undefined;
  @State maskDraw: DrawableDescriptor | undefined = undefined;
  @State maskPixel: image.PixelMap | undefined = undefined;
  @State draw: LayeredDrawableDescriptor | undefined = undefined;

  async aboutToAppear() {
    // Replace $r('app.media.foreground') with the image resource file you use.
    this.fore1 = await this.getPixmapFromMedia($r('app.media.foreground'));
    // Replace $r('app.media.background') with the image resource file you use.
    this.back1 = await this.getPixmapFromMedia($r('app.media.background'));
    // Replace $r('app.media.ohos_icon_mask') with the image resource file you use.
    this.maskPixel = await this.getPixmapFromMedia($r('app.media.ohos_icon_mask'));
    // Create a LayeredDrawableDescriptor object using PixelMapDrawableDescriptor.
    this.foregroundDraw = new PixelMapDrawableDescriptor(this.fore1);
    this.backgroundDraw = new PixelMapDrawableDescriptor(this.back1);
    this.maskDraw = new PixelMapDrawableDescriptor(this.maskPixel);
    this.draw = new LayeredDrawableDescriptor(this.foregroundDraw,this.backgroundDraw,this.maskDraw);
  }

  build() {
    Row() {
      Column() {
          Image(this.draw)
            .width(300)
            .height(300)
      }.height('100%').justifyContent(FlexAlign.Center)
    }.width('100%').height("100%").backgroundColor(Color.Pink)
  }
  // Obtain pixelMap from a resource through the image framework based on the resource.
  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let createPixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.BGRA_8888
    });
    await imageSource.release();
    return createPixelMap;
  }
}
```

### constructor<sup>12+</sup>

constructor(foreground?: DrawableDescriptor, background?: DrawableDescriptor, mask?: DrawableDescriptor)

A constructor used to create a **LayeredDrawableDescriptor** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type             | Mandatory | Description                                      |
| --------- | ---------------- | ---- | ------------------------------------------ |
| foreground | [DrawableDescriptor](#drawabledescriptor)  | No  | Options for the foreground image of the layered drawable.|
| background   | [DrawableDescriptor](#drawabledescriptor) | No  | Options for the background image of the layered drawable. |
| mask | [DrawableDescriptor](#drawabledescriptor) | No| Options for the mask of the layered drawable.|

### getForeground
getForeground(): DrawableDescriptor

Obtains the **DrawableDescriptor** object of the foreground.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                  |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | **DrawableDescriptor** object.|

**Example**
```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getForeground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // Replace $r('app.media.drawable') with the image resource file you use.
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    if (drawable instanceof LayeredDrawableDescriptor) {
      let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getForeground();
      return layeredDrawableDescriptor;
    }
    return undefined;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getForeground();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
          .borderWidth(1)
          .backgroundColor(Color.Green);
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### getBackground

getBackground(): DrawableDescriptor

Obtains the **DrawableDescriptor** object of the background.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                  |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | **DrawableDescriptor** object.|

**Example**
```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getBackground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // Replace $r('app.media.drawable') with the image resource file you use.
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getBackground();
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getBackground();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### getMask

getMask(): DrawableDescriptor

Obtains the **DrawableDescriptor** object of the mask.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                  |
| ---------------------------------------- | -------------------- |
| [DrawableDescriptor](#drawabledescriptor) | **DrawableDescriptor** object.|

**Example**
```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getMask(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // Replace $r('app.media.drawable') with the image resource file you use.
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getMask();
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.getMask();
  }

  build() {
    RelativeContainer() {
      if (this.drawableDescriptor) {
        Image(this.drawableDescriptor)
          .width(100)
          .height(100)
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### getMaskClipPath

static getMaskClipPath(): string

Obtains the built-in clipping path parameters of the system. It is a static method of **LayeredDrawableDescriptor**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description                  |
| ---------------------------------------- | -------------------- |
| string | String of the clipping path.|

**Example**

```ts
// xxx.ets
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        // Replace $r('app.media.icon') with the image resource file you use.
        Image($r('app.media.icon'))
          .width('200px').height('200px')
          .clipShape(new Path({commands:LayeredDrawableDescriptor.getMaskClipPath()}))
        Text(`Obtain the built-in clip path parameters:`)
          .fontWeight(800)
        Text(JSON.stringify(LayeredDrawableDescriptor.getMaskClipPath()))
          .padding({ left: 20, right: 20 })
      }.height('100%').justifyContent(FlexAlign.Center)
    }.width('100%')
  }
}
```

## AnimationOptions<sup>12+</sup>

Provides the configuration options for animation playback, including the playback duration, number of playback times, and autoplay behavior.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type   | Read-Only| Optional | Description                                   |
| :--------- | :----- | :----| :----| :-------------------------------------- |
| duration   | number | No  | Yes | Total playback duration for the image sequence.<br>For **PixelMap** arrays, the default value is 1s per image. For local or application resources, the duration is determined by the playback delay embedded in the image resource.<br>Unit: ms.<br> Value range: [0, +∞).<br>Negative values are treated as the default value.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| iterations | number | No  | Yes|Number of playback times for the image sequence.<br>A value of **-1** indicates infinite playback, **0** indicates no playback, and a value greater than 0 represents the number of playback times.<br>The default value is **1**.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| frameDurations<sup>21+</sup> | Array\<number> | No| Yes|Per-frame playback duration. The setting overrides **duration** if specified.<br>If **duration** and **frameDurations** are set, **duration** is ignored.<br>If the value of **frameDurations** is inconsistent with the image count, animation timing distributes across the total duration.<br>Unit: ms.<br> **Atomic service API**: This API can be used in atomic services since API version 21.|
| autoPlay<sup>21+</sup> | boolean | No | Yes|Whether to enable autoplay.<br> **true** to enable, **false** otherwise.<br>The default value is **true**.<br> **Atomic service API**: This API can be used in atomic services since API version 21.|

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct Example {
  pixelMaps: Array<image.PixelMap> = [];
  // Configure animation options for an array of four images.
  options: AnimationOptions = {
    duration: 2000,
    iterations: 1,
    frameDurations: [20, 30, 40, 50],
    autoPlay: true
  };
  @State animated?: DrawableDescriptor = undefined;

  aboutToAppear() {
    // Replace $r('app.media.png1') with the image resource file you use.
    this.pixelMaps.push(this.getPixmapFromMedia($r('app.media.png1')));
     // Replace $r('app.media.png2') with the image resource file you use.
    this.pixelMaps.push(this.getPixmapFromMedia($r('app.media.png2')));
     // Replace $r('app.media.png3') with the image resource file you use.
    this.pixelMaps.push(this.getPixmapFromMedia($r('app.media.png3')));
     // Replace $r('app.media.png4') with the image resource file you use.
    this.pixelMaps.push(this.getPixmapFromMedia($r('app.media.png4')));
    this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
  }

  build() {
    Column() {
      Row() {
        Image(this.animated)
          .width(100)
          .height(100)
      }
    }
  }

  private getPixmapFromMedia(resource: Resource) {
    let unit8Array = this.getUIContext().getHostContext()?.resourceManager?.getMediaContentSync(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let pixelMap: image.PixelMap = imageSource.createPixelMapSync({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    imageSource.release();
    return pixelMap;
  }
}
```

## AnimatedDrawableDescriptor<sup>12+</sup>

Defines a descriptor object used to play animated content (for example, **PixelMap** arrays or animated image resources) using the [Image](./arkui-ts/ts-basic-components-image.md) component. It inherits from [DrawableDescriptor](#drawabledescriptor).

### constructor<sup>12+</sup>

constructor(pixelMaps: Array\<image.PixelMap>, options?: AnimationOptions)

A constructor used to create an **AnimatedDrawableDescriptor** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type             | Mandatory | Description                                      |
| --------- | ---------------- | ---- | ------------------------------------------ |
| pixelMaps | Array\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)>  | Yes  | **PixelMap** image data.|
| options   | [AnimationOptions](#animationoptions12) | No  | Animation options.                              |

### constructor<sup>21+</sup>

constructor(src: ResourceStr | Array\<image.PixelMap>, options?: AnimationOptions)

A constructor used to create an **AnimatedDrawableDescriptor** instance.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type             | Mandatory | Description                                      |
| --------- | ---------------- | ---- | ------------------------------------------ |
| src | ResourceStr \| Array\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)> | Yes  | Animated image source address or [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) array.<br> The address (**ResourceStr**) supports the following formats: application resources (**Resource**), sandbox path (file://\<bundleName>/\<sandboxPath>), and Base64 string.|
| options   | [AnimationOptions](#animationoptions12) | No  | Animation playback configuration.|

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // Sandbox paths (file://xx) and application resources are supported.
  @State animated1: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);
  @State animated2: AnimatedDrawableDescriptor | undefined = undefined;

  aboutToAppear() {
    let files = this.getUIContext().getHostContext()?.filesDir
    let originPath = files + "/flower.gif"
    let resultPath = fileUri.getUriFromPath(originPath)
    this.animated2 = new AnimatedDrawableDescriptor(resultPath, { iterations: -1 })
  }

  build() {
    Column() {
      Row() {
        Image(this.animated1).width(100).height(100)
        Image(this.animated2).width(100).height(100)
      }
    }
  }
}
```

### getAnimationController<sup>21+</sup>

getAnimationController(id?: string): AnimationController | undefined

Obtains the animation controller for playback control.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| id     | string | No  | ID of the target component.<br>Optional when the [Image](./arkui-ts/ts-basic-components-image.md) component and **AnimatedDrawableDescriptor** object have a 1:1 relationship.<br>Required when the same **AnimatedDrawableDescriptor** object is bound to multiple [Image](./arkui-ts/ts-basic-components-image.md) components (in this case, you must ensure the ID uniqueness).<br>This rule is based on the design principle of the animation system: Animation data can be shared across multiple components, but each component's animation runs independently. Correspondingly, an **AnimationController** object maintains a strict 1:1 relationship with a component, meaning one component is paired with exactly one **AnimationController** object.<br>In addition, [AnimatedDrawableDescriptor](#animateddrawabledescriptor12) supports the feature for automatically pausing animation playback when the bound component is not visible (for example, when the component is scrolled out of the screen or hidden). For specific implementation details, see [onVisibleAreaChange](./arkui-ts/ts-universal-component-visible-area-change-event.md#onvisibleareachange).|

**Return value**

| Type            | Description                              |
| ---------------- | -----------------------------------|
| [AnimationController](#animationcontroller21) \| undefined | Animation controller object.|

**Example**

Scenario 1: 1:1 relationship between the [Image](./arkui-ts/ts-basic-components-image.md) component and **AnimatedDrawableDescriptor** object

```ts
import { AnimationOptions, AnimatedDrawableDescriptor, AnimationController } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .borderColor(Color.Red)
        .borderWidth(1)
      Button("start")
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          controller?.start()
        })
      Button("stop")
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          controller?.stop()
        })
    }
  }
}
```

Scenario 2: 1:*N* relationship between the [Image](./arkui-ts/ts-basic-components-image.md) component and **AnimatedDrawableDescriptor** object

```ts
import { AnimationOptions, AnimatedDrawableDescriptor, AnimationController } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .borderColor(Color.Red)
        .borderWidth(1)
        .id("Component1")
      Image(this.animated)
        .width(100)
        .height(100)
        .borderColor(Color.Red)
        .borderWidth(1)
      Button("start")
        .onClick(() => {
          let controller = this.animated.getAnimationController("Component1")
          controller?.start()
        })
      Button("stop")
        .onClick(() => {
          let controller = this.animated.getAnimationController("Component1")
          controller?.stop()
        })
    }
  }
}
```

## AnimationController<sup>21+</sup>

Implements an animation controller object. Provides animation playback control and status query APIs.

### start<sup>21+</sup>

start(): void

Starts playback from the first frame.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Start playback.
          controller?.start()
        })
    }
  }
}
```

### stop<sup>21+</sup>

stop(): void

Stops playback and resets to the first frame.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Stop playback and reset to the first frame.
          controller?.stop()
        })
    }
  }
}
```

### resume<sup>21+</sup>

resume(): void

Resumes playback from the current frame.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Start playback from the current frame when the animated image is paused or stopped.
          controller?.resume()
        })
    }
  }
}
```

### pause<sup>21+</sup>

pause(): void

Pauses playback on the current frame.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Pause playback on the current frame.
          controller?.pause()
        })
    }
  }
}
```

### getStatus<sup>21+</sup>

getStatus(): AnimationStatus

Obtains the current animation playback status.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                              |
| ---------------- | -----------------------------------|
| [AnimationStatus](./arkui-ts/ts-appendix-enums.md#animationstatus) | Current animation state:  initial, running, paused, or stopped.|

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  statusToString(status: AnimationStatus): string {
    switch (status) {
      case AnimationStatus.Initial:
        return "Initial"
      case AnimationStatus.Running:
        return "Running"
      case AnimationStatus.Paused:
        return "Paused"
      case AnimationStatus.Stopped:
        return "Stopped"
      default:
        return "Error"
    }
  }

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Obtain the current animation playback status.
          let status = controller?.getStatus()
          console.info(`animation status = ${this.statusToString(status)}`)
        })
    }
  }
}
```
