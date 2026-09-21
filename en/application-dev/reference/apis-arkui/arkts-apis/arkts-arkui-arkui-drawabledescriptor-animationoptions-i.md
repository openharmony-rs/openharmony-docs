# AnimationOptions

```TypeScript
declare interface AnimationOptions
```

Provides the configuration options for animation playback, including the playback duration, number of playback times, and autoplay behavior.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## autoPlay

```TypeScript
autoPlay?: boolean
```

Whether to enable autoplay.

**true** to enable, **false** otherwise.

The default value is **true**.

**Type:** boolean

**Default:** true

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Total playback duration for the image sequence.

For **PixelMap** arrays, the default value is 1s per image. For local or application resources, the duration is determined by the playback delay embedded in the image resource.

Unit: ms.

Value range: [0, +∞).

Negative values are treated as the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## frameDurations

```TypeScript
frameDurations?: Array<number>
```

Per-frame playback duration. The setting overrides **duration** if specified.

If **duration** and **frameDurations** are set, **duration** is ignored.

If the value of **frameDurations** is inconsistent with the image count, animation timing distributes across the total duration.

Unit: ms.

**Type:** Array&lt;number&gt;

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

Number of playback times for the image sequence.

A value of **-1** indicates infinite playback, **0** indicates no playback, and a value greater than 0 represents the number of playback times.

The default value is **1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stopMode

```TypeScript
stopMode?: AnimationStopMode
```

Sets the stop mode for an animation.

The default value is **AnimationStopMode.FIRST_FRAME**, indicating that the animation returns to the first frame when it stops.

**Type:** [AnimationStopMode](arkts-arkui-arkui-drawabledescriptor-animationstopmode-e.md)

**Default:** AnimationStopMode.FIRST_FRAME

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor, DrawableDescriptor } from '@kit.ArkUI';
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
