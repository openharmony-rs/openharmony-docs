# PictureDrawableDescriptor

支持通过传入Picture对象创建PictureDrawableDescriptor对象。 继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** PictureDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(src: image.Picture)
```

PictureDrawableDescriptor的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.Picture | 是 | 用于创建PictureDrawableDescriptor的Picture对象。 |

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

## setHdrComposition

```TypeScript
setHdrComposition(config: HdrCompositionConfig): void
```

设置HDR合成配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [HdrCompositionConfig](arkts-arkui-arkui-drawabledescriptor-hdrcompositionconfig-i.md) | 是 | HDR合成配置。 |

**示例**

```TypeScript
import { PictureDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';


@Entry
@Component
struct PictureDrawableDescriptorInvalidateTest {
  @State drawable: PictureDrawableDescriptor | undefined = undefined;

  async createPictureDrawableDescriptor() {
    let resMgr = this.getUIContext().getHostContext()?.resourceManager
    if (resMgr) {
      try {
        // $r('app.media.heic')需要替换为开发者所需的图像资源文件。
        let uint8buffer = resMgr.getMediaContentSync($r('app.media.heic').id)
        let imageSource = image.createImageSource(uint8buffer.buffer)
        // 配置解码选项，请求解码GAINMAP和LHDR_GAINMAP辅助图用于HDR合成。
        let options: image.DecodingOptionsForPicture = {
          desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP, image.AuxiliaryPictureType.LHDR_GAINMAP],
          desiredPixelFormat: image.PixelMapFormat.NV12
        }
        let picture = await imageSource.createPicture(options)
        let drawable = new PictureDrawableDescriptor(picture)
        imageSource.release()
        this.drawable = drawable
      } catch (error) {
        console.error(`get media content failed`)
      }
    }
  }

  build() {
    Column() {
      Image(this.drawable)
        .width(300)
        .height(225)
        .borderColor(Color.Red)
        .borderWidth(1)

      Button("创建PictureDrawableDescriptor对象").onClick((event: ClickEvent) => {
        this.createPictureDrawableDescriptor()
      })

      Button("触发一次重建").onClick((event: ClickEvent) => {
        // 设置HDR合成配置，指定合成矩形区域的位置和大小。
        this.drawable?.setHdrComposition({
          rect: {
            x: 200,
            y: 200,
            width: 300,
            height: 300
          }
        })
        this.drawable?.invalidate()
      })
    }
    .height('100%')
    .width('100%')
  }
}
```
