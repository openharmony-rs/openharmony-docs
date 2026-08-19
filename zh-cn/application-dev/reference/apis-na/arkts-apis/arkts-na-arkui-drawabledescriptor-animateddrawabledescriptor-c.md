# AnimatedDrawableDescriptor

使用Image组件播放PixelMap数组或动图资源时传入 AnimatedDrawableDescriptor对象，该对象继承自[DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** AnimatedDrawableDescriptor extends [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class AnimatedDrawableDescriptor--><!--Device-unnamed-export declare class AnimatedDrawableDescriptor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)
```

AnimatedDrawableDescriptor的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatedDrawableDescriptor-constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)--><!--Device-AnimatedDrawableDescriptor-constructor(pixelMaps: Array<image.PixelMap>, options?: AnimationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelMaps | Array&lt;image.PixelMap&gt; | 是 | PixelMap 数组类型参数，存储 PixelMap 图片数据。 |
| options | [AnimationOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 否 | 动画控制选项。 |

## constructor

```TypeScript
constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)
```

AnimatedDrawableDescriptor的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatedDrawableDescriptor-constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)--><!--Device-AnimatedDrawableDescriptor-constructor(src: ResourceStr | Array<image.PixelMap>, options?: AnimationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | ResourceStr \| Array&lt;image.PixelMap&gt; | 是 | 动图资源地址或者 [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)对象构成的数组。<br/> ResourceStr当前支持的范围： 应用资源Resource，沙箱路径（file://&lt;bundleName&gt;/&lt;sandboxPath&gt;），BASE64字符串。 |
| options | [AnimationOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-animationoptions-i.md) | 否 | 动画控制参数。 |

## getAnimationController

```TypeScript
getAnimationController(id?: string): AnimationController | undefined
```

获取动画控制器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatedDrawableDescriptor-getAnimationController(id?: string): AnimationController | undefined--><!--Device-AnimatedDrawableDescriptor-getAnimationController(id?: string): AnimationController | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 否 | 组件的id。<br/>当Image组件与 AnimatedDrawableDescriptor确保1比1持有（仅传入一个Image组件）时， id非必填；<br/>若同一AnimatedDrawableDescriptor需绑定多个 Image组件，则必须设置唯一id以准确获取对应组件的动画控制器 （唯一性由开发者保证）。<br/>此规则基于动画系统设计原则：动画数据可多组件共享，但各组件动画独立运行， AnimationController与组件严格1比1持有关系（一个组件一个AnimationController对象）。<br/>另外， [AnimatedDrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)支持不可见时自动暂停播放功能，详见 onVisibleAreaChange。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimationController](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-animationcontroller-i.md) | Return the component of animation controller. |

