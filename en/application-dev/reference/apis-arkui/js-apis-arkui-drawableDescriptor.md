# @ohos.arkui.drawableDescriptor (DrawableDescriptor)

The **DrawableDescriptor** module provides APIs for obtaining **pixelMap** objects, including the foreground, background, mask, and layered icons.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

## Modules to Import

```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';
```

## DrawableDescriptor

Resources in PNG, JPG, BMP, SVG, GIF, WEBP, ASTC, and SUT formats are supported.

### getPixelMap

getPixelMap(): image.PixelMap

Obtains this **pixelMap** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                      | Description      |
| ---------------------------------------- | -------- |
| [image.PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7) | **PixelMap** object.|

**Example**
  ```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI'
let resManager = this.getUIContext().getHostContext()?.resourceManager
let pixmap: DrawableDescriptor = (resManager?.getDrawableDescriptor($r('app.media.icon')
    .id)) as DrawableDescriptor;
let pixmapNew: object = pixmap.getPixelMap()
  ```

Creates a **DrawableDescriptor** object when the passed resource ID or name belongs to a common image.

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
| src | [image.PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)  | No| **PixelMap** image data.|


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

1. Create a **LayeredDrawableDescriptor** object using a JSON file.

    ```ts
    // xxx.ets
    import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

    @Entry
    @Component
    struct Index {
      private resManager = this.getUIContext().getHostContext()?.resourceManager;
 
      build() {
        Row() {
          Column() {
            Image((this.resManager?.getDrawableDescriptor($r('app.media.drawable').id) as LayeredDrawableDescriptor))
            Image(((this.resManager?.getDrawableDescriptor($r('app.media.drawable')
            .id) as LayeredDrawableDescriptor).getForeground()).getPixelMap())
          }.height('50%')
        }.width('50%')
      }
    }
    ```
2. Create a **LayeredDrawableDescriptor** object using **PixelMapDrawableDescriptor**.
   
    ```ts
    import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor } from '@kit.ArkUI';
    import { image } from '@kit.ImageKit';

    @Entry
    @Component
    struct Index {
      @State fore1: image.PixelMap | undefined = undefined;
      @State back1: image.PixelMap | undefined = undefined;

      @State foregroundDraw:DrawableDescriptor|undefined=undefined;
      @State backgroundDraw:DrawableDescriptor|undefined=undefined;
      @State maskDraw:DrawableDescriptor|undefined=undefined;
      @State maskPixel: image.PixelMap | undefined = undefined;
      @State draw : LayeredDrawableDescriptor | undefined = undefined;
      async aboutToAppear() {
        this.fore1 = await this.getPixmapFromMedia($r('app.media.foreground'));
        this.back1 = await this.getPixmapFromMedia($r('app.media.background'));
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
      // Obtain pixelMap from a resource through the image framework based on the resource
      private async getPixmapFromMedia(resource: Resource) {
        let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent({
          bundleName: resource.bundleName,
          moduleName: resource.moduleName,
          id: resource.id
        });
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
    let drawable: DrawableDescriptor | undefined = resManager?.getDrawableDescriptor($r('app.media.drawable').id);
    if (!drawable) {
      return undefined;
    }
    let layeredDrawableDescriptor = (drawable as LayeredDrawableDescriptor).getForeground();
    return layeredDrawableDescriptor;
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

Configures the playback behavior of **PixelMap** array animations displayed through the **Image** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type   | Mandatory | Description                                   |
| ---------- | ------ | -----| --------------------------------------- |
| duration   | number | No  | Total playback duration for the **PixelMap** array animation. By default, each image is played for 1 second.<br> Value range: [0, +∞).     |
| iterations | number | No  | Number of times that the **PixelMap** array animation is played. The default value is **1**. A value of **-1** indicates infinite playback, **0** indicates no playback, and a value greater than 0 represents the number of playback times.|

**Example**

```ts
import { AnimationOptions } from '@kit.ArkUI';
@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 2000, iterations: 1 };
  build() {
  }
}
```

## AnimatedDrawableDescriptor<sup>12+</sup>

Extends [DrawableDescriptor](#drawabledescriptor) to provide the capability for animating **PixelMap** arrays displayed using the **Image** component.

### constructor<sup>12+</sup>

constructor(pixelMaps: Array\<image.PixelMap>, options?: AnimationOptions)

A constructor used to create an **AnimatedDrawableDescriptor** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type             | Mandatory | Description                                      |
| --------- | ---------------- | ---- | ------------------------------------------ |
| pixelMaps | Array\<[image.PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)>  | Yes  | **PixelMap** image data.|
| options   | [AnimationOptions](#animationoptions12) | No  | Animation options.                              |

**Example**

```ts
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct Example {
  pixelmaps: Array<image.PixelMap>  = [];
  options: AnimationOptions = {duration:1000, iterations:-1};
  @State animated: AnimatedDrawableDescriptor  = new AnimatedDrawableDescriptor(this.pixelmaps, this.options);
  async aboutToAppear() {
    this.pixelmaps.push(await this.getPixmapFromMedia($r('app.media.icon')));
    this.animated = new AnimatedDrawableDescriptor(this.pixelmaps, this.options);
  }
  build() {
    Column() {
      Row() {
        Image(this.animated)
      }
    }
  }
  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent({
      bundleName: resource.bundleName,
      moduleName: resource.moduleName,
      id: resource.id
    });
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let createPixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return createPixelMap;
  }
}

```
