# DrawableDescriptorLoadedResult

传入的图片资源或地址的加载结果。

**起始版本：** 21

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## imageHeight

```TypeScript
imageHeight: number
```

图片的高度。单位：px

**类型：** number

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageWidth

```TypeScript
imageWidth: number
```

图片的宽度。单位：px

**类型：** number

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { AnimatedDrawableDescriptor, AnimationOptions, DrawableDescriptor, DrawableDescriptorLoadedResult } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  options: AnimationOptions = { duration: 2000, iterations: 1 };
  // $r('app.media.gif')需要替换为开发者所需的图像资源文件。
  @State drawable: DrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);
  @State result: string = '';

  aboutToAppear() {
    // 在页面显示前提前加载资源到内存中，加快Image组件渲染速度。
    // 使用loadSync同步加载：
    // let loadResult: DrawableDescriptorLoadedResult = this.drawable.loadSync()
    // 使用load异步加载：
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
