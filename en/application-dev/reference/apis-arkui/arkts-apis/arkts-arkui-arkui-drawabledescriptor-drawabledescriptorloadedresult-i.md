# DrawableDescriptorLoadedResult

```TypeScript
export interface DrawableDescriptorLoadedResult
```

Represents the result of loading an image resource or URI.

**Since:** 21

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## imageHeight

```TypeScript
imageHeight: number
```

Image height.

Unit: px.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageWidth

```TypeScript
imageWidth: number
```

Image width.

Unit: px.

**Type:** number

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimatedDrawableDescriptor, AnimationOptions, DrawableDescriptor, DrawableDescriptorLoadedResult } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  options: AnimationOptions = { duration: 2000, iterations: 1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State drawable: DrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);
  @State result: string = '';

  aboutToAppear() {
    // Load resources to the memory before the page is displayed to speed up the rendering of the Image component.
    // Use loadSync for synchronous loading:
    // let loadResult: DrawableDescriptorLoadedResult = this.drawable.loadSync()
    // Use load for asynchronous loading:
    this.drawable.load().then((loadResult: DrawableDescriptorLoadedResult) => {
      this.result = `width: ${loadResult.imageWidth}, height: ${loadResult.imageHeight}`
      console.info(`load result = ${JSON.stringify(loadResult)}`)
    }).catch(() => {
      console.error("load failed")
    })
  }

  build() {
    Column() {
      Image(this.drawable)
        .width(100)
        .height(100)
      Text(this.result)
    }
  }
}
```
