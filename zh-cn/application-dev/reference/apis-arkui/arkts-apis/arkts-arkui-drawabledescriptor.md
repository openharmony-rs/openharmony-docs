# @ohos.arkui.drawableDescriptor

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AnimatedDrawableDescriptor](arkts-arkui-animateddrawabledescriptor-c.md) | 使用[Image](./@internal/component/ets/image)组件播放PixelMap数组或动图资源时传入<br/>AnimatedDrawableDescriptor对象，<br/>该对象继承自[DrawableDescriptor](arkts-arkui-drawabledescriptorloadedresult-i.md#DrawableDescriptorLoadedResult)。<br/> |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-c.md) | 父类对象提供可重写的方法，包含：获取[PixelMap](@ohos.multimedia.image:image.PixelMap)实例，图片资源加载能力。<br/> |
| <!--DelRow-->[DrawableDescriptor](arkts-arkui-drawabledescriptor-c-sys.md) | 父类对象提供可重写的方法，包含：获取[PixelMap](@ohos.multimedia.image:image.PixelMap)实例，图片资源加载能力。<br/> |
| [LayeredDrawableDescriptor](arkts-arkui-layereddrawabledescriptor-c.md) | 当传入资源id或name为包含前景和背景资源的json文件时，生成LayeredDrawableDescriptor对象。继承自<br/>[DrawableDescriptor](arkts-arkui-drawabledescriptorloadedresult-i.md#DrawableDescriptorLoadedResult)。<br/><br/>drawable.json位于项目工程entry/src/main/resources/base/media目录下。定义请参考：<br/> |
| [PictureDrawableDescriptor](arkts-arkui-picturedrawabledescriptor-c.md) | 支持通过传入Picture对象创建PictureDrawableDescriptor对象。<br/>继承自[DrawableDescriptor](arkts-arkui-drawabledescriptorloadedresult-i.md#DrawableDescriptorLoadedResult)。<br/> |
| [PixelMapDrawableDescriptor](arkts-arkui-pixelmapdrawabledescriptor-c.md) | 支持通过传入PixelMap创建PixelMapDrawableDescriptor对象。<br/>继承自[DrawableDescriptor](arkts-arkui-drawabledescriptorloadedresult-i.md#DrawableDescriptorLoadedResult)。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AnimationController](arkts-arkui-animationcontroller-i.md) | 动画控制器对象。包含控制动画播放、停止、恢复、暂停和状态查询等方法。<br/> |
| [AnimationOptions](arkts-arkui-animationoptions-i.md) | 动画播放参数。包括播放时延，迭代次数，单帧播放时间，是否自动播放。<br/> |
| [DrawableDescriptorLoadedResult](arkts-arkui-drawabledescriptorloadedresult-i.md) | 传入的图片资源或地址的加载结果。<br/> |
| [HdrCompositionConfig](arkts-arkui-hdrcompositionconfig-i.md) | HDR合成配置选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AnimationStopMode](arkts-arkui-animationstopmode-e.md) | 动图停止模式。<br/> |

