# PixelMapDrawableDescriptor

支持通过传入PixelMap创建PixelMapDrawableDescriptor对象。 继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** PixelMapDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(src?: image.PixelMap)
```

PixelMapDrawableDescriptor的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap | 否 | PixelMap类型参数，存储 PixelMap 图片数据。 |

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

## constructor

```TypeScript
constructor(src?: image.PixelMap | ResourceStr)
```

PixelMapDrawableDescriptor的构造函数，通过PixelMap类型或者ResourceStr创建。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | image.PixelMap \| [ResourceStr](arkts-arkui-resourcestr-t.md) | 否 | PixelMap类型参数，存储PixelMap图片数据。支持应用资源、系统资源、沙箱路径（file:// & lt;bundleName & gt;/ & lt;sandboxPath & gt;） 和Base64字符串用于创建PixelMapDrawableDescriptor。 |

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
