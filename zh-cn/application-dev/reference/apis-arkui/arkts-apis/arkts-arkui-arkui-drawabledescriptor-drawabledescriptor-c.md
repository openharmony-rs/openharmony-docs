# DrawableDescriptor

父类对象提供可重写的方法，包含：获取[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)实例，图片资源加载能力。

**起始版本：** 10

<!--Device-unnamed-export class DrawableDescriptor--><!--Device-unnamed-export class DrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, AnimatedDrawableDescriptor, AnimationStopMode, AnimationOptions, AnimationController, DrawableDescriptorLoadedResult, LayeredDrawableDescriptor, PictureDrawableDescriptor, PixelMapDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## getPixelMap

```TypeScript
getPixelMap(): image.PixelMap
```

获取PixelMap实例。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-getPixelMap(): image.PixelMap--><!--Device-DrawableDescriptor-getPixelMap(): image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | PixelMap |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例：**

示例请参考[LayeredDrawableDescriptor](#layereddrawabledescriptor)中的示例代码。

## invalidate

```TypeScript
invalidate(): void
```

重新绘制DrawableDescriptor。当前仅支持[PictureDrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-picturedrawabledescriptor-c.md)类型，其他DrawableDescriptor子类型触发后无效果。若DrawableDescriptor未绑定任何组件，则不会执行任何操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-invalidate(): void--><!--Device-DrawableDescriptor-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isReleased

```TypeScript
isReleased(): boolean
```

查询DrawableDescriptor是否已被释放。返回true表示已释放，此时调用[getPixelMap](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#getpixelmap)、[getForeground](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getforeground)、[getBackground](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getbackground)、[getMask](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getmask)、[loadSync](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#loadsync)、[load](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#load)等接口会抛出111002错误；返回false表示未释放，对象可正常使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-isReleased(): boolean--><!--Device-DrawableDescriptor-isReleased(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | DrawableDescriptor是否已被释放。true表示已释放，false表示未释放。 |

## load

```TypeScript
load(): Promise<DrawableDescriptorLoadedResult>
```

发起图片资源的异步加载，并返回加载结果。使用Promise异步回调。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-load(): Promise<DrawableDescriptorLoadedResult>--><!--Device-DrawableDescriptor-load(): Promise<DrawableDescriptorLoadedResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DrawableDescriptorLoadedResult&gt; | 图片资源的加载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111001](../errorcode-drawable-descriptor.md#111001-资源加载失败) | resource loading failed. |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例：**

示例请参考[DrawableDescriptorLoadedResult](#drawabledescriptorloadedresult21)中的示例代码。

## loadSync

```TypeScript
loadSync(): DrawableDescriptorLoadedResult
```

发起图片资源的同步加载，并返回加载结果。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-loadSync(): DrawableDescriptorLoadedResult--><!--Device-DrawableDescriptor-loadSync(): DrawableDescriptorLoadedResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawableDescriptorLoadedResult](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md) | 图片资源的加载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [111001](../errorcode-drawable-descriptor.md#111001-资源加载失败) | resource loading failed. |
| [111002](../errorcode-drawable-descriptor.md#111002-资源已释放) | The native memory referenced by the drawableDescriptor has been released.<br>**适用版本：** 26.0.0+ |

**示例：**

示例请参考[DrawableDescriptorLoadedResult](#drawabledescriptorloadedresult21)中的示例代码。

## release

```TypeScript
release(): void
```

释放DrawableDescriptor持有的资源。调用release后，该对象将不可用，再调用[getPixelMap](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#getpixelmap)、[getForeground](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getforeground)、[getBackground](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getbackground)、[getMask](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md#getmask)、[loadSync](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#loadsync)、[load](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md#load)等接口会抛出111002错误。重复调用release不会崩溃。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DrawableDescriptor-release(): void--><!--Device-DrawableDescriptor-release(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
import { DrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private resManager = this.getUIContext().getHostContext()?.resourceManager;
  // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
  private drawable: DrawableDescriptor | undefined =
    this.resManager?.getDrawableDescriptor($r('app.media.startIcon').id);

  build() {
    Column() {
      Button('release')
        .onClick(() => {
          this.drawable?.release()
        })
      Button('isReleased')
        .onClick(() => {
          let released = this.drawable?.isReleased()
          console.info(`isReleased = ${released}`)
        })
    }
  }
}

```

