# AnimatedDrawableDescriptor

Defines a descriptor object used to play animated content (for example, **PixelMap** arrays or animated image resources) using the Image component. It inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md).

**Inheritance/Implementation:** AnimatedDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)
```

A constructor used to create an **AnimatedDrawableDescriptor** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelMaps | Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | **PixelMap** image data. |
| options | [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | No | Animation options. |

**Examples**

```TypeScript
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

## constructor

```TypeScript
constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)
```

A constructor used to create an **AnimatedDrawableDescriptor** object.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [ResourceStr](arkts-arkui-resourcestr-t.md) &#124; Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Animated image source address or [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) array.<br> The address (**ResourceStr**) supports the following formats: application resources (**Resource**), sandbox path (file://&lt;bundleName&gt;/&lt;sandboxPath&gt;), and Base64 string. |
| options | [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | No | Animation playback configuration. |

**Examples**

```TypeScript
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

## getAnimationController

```TypeScript
getAnimationController(id?: string): AnimationController | undefined
```

Obtains the animation controller for playback control.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | No | ID of the target component.<br>Optional when the Image component and **AnimatedDrawableDescriptor** object have a 1:1 relationship.<br>Required when the same **AnimatedDrawableDescriptor** object is bound to multiple Image components (in this case, you must ensure the ID uniqueness).<br>This rule is based on the design principle of the animation system: Animation data can be shared across multiple components, but each component's animation runs independently. Correspondingly, an **AnimationController** object maintains a strict 1:1 relationship with a component, meaning one component is paired with exactly one **AnimationController** object.<br>In addition, [AnimatedDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) supports the feature for automatically pausing animation playback when the bound component is not visible (for example, when the component is scrolled out of the screen or hidden). For specific implementation details, see [onVisibleAreaChange] [onVisibleAreaChange](../arkts-components/arkts-arkui-commonmethod-c.md#onvisibleareachange). |

**Return value:**

| Type | Description |
| --- | --- |
| [AnimationController](arkts-arkui-arkui-drawabledescriptor-animationcontroller-i.md) &#124; undefined | Animation controller object. |

**Examples**

```TypeScript
Scenario 1: 1:1 relationship between the [Image](../arkui-ts/ts-basic-components-image.md) component and AnimatedDrawableDescriptor object
```

```TypeScript
Scenario 2: 1:N relationship between the [Image](../arkui-ts/ts-basic-components-image.md) component and AnimatedDrawableDescriptor object
```
