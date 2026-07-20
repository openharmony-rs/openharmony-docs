# AnimatedDrawableDescriptor

使用[Image](../../apis-arkui/arkts-components/arkts-arkui-image-i)组件播放PixelMap数组或动图资源时传入AnimatedDrawableDescriptor对象，该对象继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** AnimatedDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 12

<!--Device-unnamed-export class AnimatedDrawableDescriptor extends DrawableDescriptor--><!--Device-unnamed-export class AnimatedDrawableDescriptor extends DrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, AnimatedDrawableDescriptor, AnimationStopMode, AnimationOptions, AnimationController, DrawableDescriptorLoadedResult, LayeredDrawableDescriptor, PictureDrawableDescriptor, PixelMapDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)
```

AnimatedDrawableDescriptor的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatedDrawableDescriptor-constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)--><!--Device-AnimatedDrawableDescriptor-constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelMaps | Array&lt;image.PixelMap&gt; | 是 | PixelMap 数组类型参数，存储 PixelMap 图片数据。 |
| options | [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 否 | 动画控制选项。 |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)
```

AnimatedDrawableDescriptor的构造函数。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatedDrawableDescriptor-constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)--><!--Device-AnimatedDrawableDescriptor-constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [ResourceStr](arkts-arkui-resourcestr-t.md) \| Array&lt;image.PixelMap&gt; | 是 | 动图资源地址或者[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)对象构成的数组。<br/> ResourceStr当前支持的范围：应用资源Resource，沙箱路径（file://<bundleName>/<sandboxPath>），BASE64字符串。 |
| options | [AnimationOptions](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 否 | 动画控制参数。 |

**示例：**

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

<a id="getanimationcontroller"></a>
## getAnimationController

```TypeScript
getAnimationController(id?: string): AnimationController | undefined
```

获取动画控制器。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-AnimatedDrawableDescriptor-getAnimationController(id?: string): AnimationController | undefined--><!--Device-AnimatedDrawableDescriptor-getAnimationController(id?: string): AnimationController | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 否 | 组件的id。<br/>当[Image](../../apis-arkui/arkts-components/arkts-arkui-image-i)组件与AnimatedDrawableDescriptor确保1比1持有（仅传入一个[Image](../../apis-arkui/arkts-components/arkts-arkui-image-i)组件）时，id非必填；<br/>若同一AnimatedDrawableDescriptor需绑定多个[Image](../../apis-arkui/arkts-components/arkts-arkui-image-i)组件，则必须设置唯一id以准确获取对应组件的动画控制器（唯一性由开发者保证）。<br/>此规则基于动画系统设计原则：动画数据可多组件共享，但各组件动画独立运行，AnimationController与组件严格1比1持有关系（一个组件一个AnimationController对象）。<br/>另外，[AnimatedDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)支持不可见时自动暂停播放功能，详见[onVisibleAreaChange](../arkts-components/arkts-arkui-commonmethod-c.md#onvisibleareachange-1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimationController](arkts-arkui-arkui-drawabledescriptor-animationcontroller-i.md) | 动画控制器对象。 |

**示例：**

[Image](./arkui-ts/ts-basic-components-image.md)组件与AnimatedDrawableDescriptor保持1比1持有关系，示例代码如下。

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor, AnimationController } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // $r('app.media.gif')需要替换为开发者所需的图像资源文件。
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

[Image](./arkui-ts/ts-basic-components-image.md)组件与AnimatedDrawableDescriptor保持1比N持有关系，示例代码如下。

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor, AnimationController } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // $r('app.media.gif')需要替换为开发者所需的图像资源文件。
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

