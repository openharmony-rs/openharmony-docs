# @ohos.arkui.drawableDescriptor(DrawableDescriptor)

本模块提供分层图标合成（包括前景，背景，蒙版），动图播放与控制，基础图像处理的能力。
 > **说明：**
 >
 > - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。


## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AnimatedDrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) | 使用Image组件播放PixelMap数组或动图资源时传入 AnimatedDrawableDescriptor对象， 该对象继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。 |
| [DrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | 父类对象提供可重写的方法，包含：获取[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)实例，图片资源加载能力。 |
| [LayeredDrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md) | 当传入资源id或name为包含前景和背景资源的json文件时，生成LayeredDrawableDescriptor对象。继承自 [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。drawable.json位于项目工程entry/src/main/resources/base/media目录下。定义请参考： |
| [PictureDrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-picturedrawabledescriptor-c.md) | 支持通过传入Picture对象创建PictureDrawableDescriptor对象。 继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。 |
| [PixelMapDrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-pixelmapdrawabledescriptor-c.md) | 支持通过传入PixelMap创建PixelMapDrawableDescriptor对象。 继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DrawableDescriptor(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c-sys.md) | 父类对象提供可重写的方法，包含：获取[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)实例，图片资源加载能力。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AnimationController(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-animationcontroller-i.md) | 动画控制器对象。包含控制动画播放、停止、恢复、暂停和状态查询等方法。 |
| [AnimationOptions(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 动画播放参数。包括播放时延，迭代次数，单帧播放时间，是否自动播放。 |
| [DrawableDescriptorLoadedResult(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md) | 传入的图片资源或地址的加载结果。 |
| [HdrCompositionConfig(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-hdrcompositionconfig-i.md) | HDR合成配置选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AnimationStopMode(DrawableDescriptor)](arkts-arkui-arkui-drawabledescriptor-animationstopmode-e.md) | 动图停止模式。 |
