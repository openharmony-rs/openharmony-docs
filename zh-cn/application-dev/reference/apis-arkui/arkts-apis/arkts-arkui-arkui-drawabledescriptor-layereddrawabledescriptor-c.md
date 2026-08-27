# LayeredDrawableDescriptor

当传入资源id或name为包含前景和背景资源的json文件时，生成LayeredDrawableDescriptor对象。继承自 [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。drawable.json位于项目工程entry/src/main/resources/base/media目录下。定义请参考：

**继承/实现关系：** LayeredDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

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

LayeredDrawableDescriptor的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| foreground | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的前景图片选项。 |
| background | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的背景图片选项。 |
| mask | [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 否 | 分层图标的遮罩选项。 |

**示例**

通过ResourceStr创建PixelMapDrawableDescriptor，示例代码如下。

```TypeScript
// xxx.ets
import { DrawableDescriptor, PixelMapDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct PixelMapDrawableDescriptorExample {
  // 使用Resource创建PixelMapDrawableDescriptor
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  @State drawable: DrawableDescriptor = new PixelMapDrawableDescriptor($r('app.media.icon'))

  build() {
    Column() {
      Image(this.drawable)
        .width(100)
        .height(100)
        .margin({ bottom: 20 })
    }
  }
}
```

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // 支持传入file://xx沙箱路径和应用资源Resource。
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

## getBackground

```TypeScript
getBackground(): DrawableDescriptor
```

获取背景的DrawableDescriptor对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getBackground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // $r('app.media.drawable')需要替换为开发者所需的图像资源文件。
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

获取前景的DrawableDescriptor对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getForeground(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // $r('app.media.drawable')需要替换为开发者所需的图像资源文件。
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

获取蒙版的DrawableDescriptor对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private getMask(): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // $r('app.media.drawable')需要替换为开发者所需的图像资源文件。
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

LayeredDrawableDescriptor的静态方法，获取系统内置的裁切路径参数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回裁切路径的命令字符串。 |

**示例**

```TypeScript
// xxx.ets
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.icon'))
          .width('200px').height('200px')
          .clipShape(new Path({commands:LayeredDrawableDescriptor.getMaskClipPath()}))
        Text(`获取系统内置的裁剪路径参数：`)
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

设置LayeredDrawableDescriptor的混合模式。对同一LayeredDrawableDescriptor对象多次调用setBlendMode接口时， 仅在绘制完成前的最后一次调用生效。该接口不支持动态切换。 LayeredDrawableDescriptor的默认绘制顺序为背景、蒙版、前景。设置了混合模式后，绘制顺序变为背景、前景、蒙版。 若设置的值无效，则按照未设置混合模式进行绘制。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | drawing.BlendMode | 是 | 混合模式。 |

**示例**

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State drawableDescriptor: DrawableDescriptor | undefined = undefined;

  private setBlendMode(blendMode: drawing.BlendMode): DrawableDescriptor | undefined {
    let resManager = this.getUIContext().getHostContext()?.resourceManager;
    // $r('app.media.drawable')需要替换为开发者提供的分层图标文件。
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

**示例**

使用json文件创建LayeredDrawableDescriptor，示例代码如下。

```TypeScript
// xxx.ets
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private resManager = this.getUIContext().getHostContext()?.resourceManager;
  // $r('app.media.drawable')需要替换为开发者所需的图像资源文件。
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

使用PixelMapDrawableDescriptor创建LayeredDrawableDescriptor，示例代码如下。

```TypeScript
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
    // $r('app.media.foreground')需要替换为开发者所需的图像资源文件。
    this.fore1 = await this.getPixmapFromMedia($r('app.media.foreground'));
    // $r('app.media.background')需要替换为开发者所需的图像资源文件。
    this.back1 = await this.getPixmapFromMedia($r('app.media.background'));
    // $r('app.media.ohos_icon_mask')需要替换为开发者所需的图像资源文件。
    this.maskPixel = await this.getPixmapFromMedia($r('app.media.ohos_icon_mask'));
    // 使用PixelMapDrawableDescriptor创建LayeredDrawableDescriptor。
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
  // 根据资源，通过图片框架获取pixelMap。
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
