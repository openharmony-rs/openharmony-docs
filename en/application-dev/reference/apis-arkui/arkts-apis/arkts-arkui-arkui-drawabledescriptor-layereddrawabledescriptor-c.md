# LayeredDrawableDescriptor

Creates a **LayeredDrawableDescriptor** object when the passed resource ID or name belongs to a JSON file that contains foreground and background resources. Inherits from [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md).

The **drawable.json** file is located under **entry/src/main/resources/base/media** in the project directory. Below shows the file content:

**Inheritance/Implementation:** LayeredDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(
    foreground?: DrawableDescriptor,
    background?: DrawableDescriptor,
    mask?: DrawableDescriptor
  )
```

A constructor used to create a **LayeredDrawableDescriptor** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| foreground | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | No | Options for the foreground image of the layered drawable. |
| background | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | No | Options for the background image of the layered drawable. |
| mask | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | No | Options for the mask of the layered drawable. |

## getBackground

```TypeScript
getBackground(): DrawableDescriptor
```

Obtains the **DrawableDescriptor** object of the background.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-resource-released) | The native memory referenced by the drawableDescriptor has been released.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
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

## getForeground

```TypeScript
getForeground(): DrawableDescriptor
```

Obtains the **DrawableDescriptor** object of the foreground.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-resource-released) | The native memory referenced by the drawableDescriptor has been released.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
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

## getMask

```TypeScript
getMask(): DrawableDescriptor
```

Obtains the **DrawableDescriptor** object of the mask.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-resource-released) | The native memory referenced by the drawableDescriptor has been released.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
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

## getMaskClipPath

```TypeScript
static getMaskClipPath(): string
```

Obtains the built-in clipping path parameters of the system. It is a static method of **LayeredDrawableDescriptor**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | String of the clipping path. |

**Examples**

```TypeScript
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

## setBlendMode

```TypeScript
setBlendMode(mode: drawing.BlendMode): void
```

Sets the blend mode of **LayeredDrawableDescriptor**. If this API is called for multiple times on the same **LayeredDrawableDescriptor** object, only the last call before the drawing completion takes effect. This API does not support dynamic switching. The default drawing order of **LayeredDrawableDescriptor** is background, mask, and foreground. After the blend mode is set, the drawing order changes to background, foreground, and mask. If the specified value is invalid, the default drawing order is used.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [drawing.BlendMode](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-blendmode-e.md) | Yes | Blend mode. |

**Examples**

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private setBlendMode(blendMode: drawing.BlendMode): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // Replace $r('app.media.drawable') with the layered icon file you use.
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = drawable as LayeredDrawableDescriptor;
    layeredDrawableDescriptor.setBlendMode(blendMode);
    return layeredDrawableDescriptor;
  }

  aboutToAppear(): void {
    this.drawableDescriptor = this.setBlendMode(drawing.BlendMode.SRC_OVER);
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
