# Image

Image为图片组件，常用于在应用中显示图片。Image支持加载[PixelMap]{@link @ohos.multimedia.image:image.PixelMap}、 [ResourceStr]{@link ResourceStr}和[DrawableDescriptor]{@link DrawableDescriptor}类型的数据源，支持png、jpg、jpeg、bmp、svg、webp、gif 、heif和tiff类型的图片格式，不支持apng和svga格式。 > **说明：** > > - 从API version 23开始，图片类型新增支持tiff格式。 > > - 该组件从API版本26.0.0开始支持[WithTheme]{@link ./with_theme}。 > > - 使用快捷组合键对Image组件复制时，Image组件必须处于获焦状态，如何获焦请参考[设置组件是否可获焦](docroot://ui/arkts-common-events-focus-event.md#设置组件是否可获焦)。 > Image组件默认不获焦，需将[focusable]{@link CommonMethod#focusable}属性设置为true，即可使用Tab键将焦点切换到组件上，再将 > [focusOnTouch]{@link CommonMethod#focusOnTouch}属性设置为true，即可实现点击获焦。 > > - 图片格式支持SVG图源，SVG标签文档请参考[SVG标签说明]{@link ./common}。 > > - 动图的播放依赖于Image节点的可见性变化，其默认行为是不播放的。当节点可见时，通过回调启动动画，当节点不可见时，停止动画。可见性状态的判断是通过 > [onVisibleAreaChange]{@link CommonMethod#onVisibleAreaChange(ratios: Array<number>, event: VisibleAreaChangeCallback)} > 事件触发的，当可见阈值ratios大于0时，表明Image处于可见状态。 > > - Image组件播放GIF动图时，帧时长取自GIF文件中各帧的delay time字段。当某帧的时长值小于等于0时，系统会将其修正为100ms；当某帧的时长值大于0时，系统直接使用该原始值，不做最小帧时长限制。 需要权限 使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](docroot://security/AccessToken/declare-permissions.md)。 子组件 无

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```

通过图片数据源获取图片，用于后续渲染展示。 Image组件加载图片失败或图片尺寸为0时，图片组件大小自动为0，不跟随父组件的布局约束。 Image组件默认按照居中裁剪，例如组件宽高设置相同，原图长宽不等，此时按照中间区域进行裁剪。 Image加载成功且组件不设置宽高时，其显示大小自适应父组件。 > **说明：** > > - Image直接传入URL可能会带来的潜在性能问题，例如：(1) 大图加载时无法提前下载，白块显示的时间较长；(2) 小图设置同步加载，在弱网环境下，可能会阻塞UI线程造成冻屏问题；(3) 在快速滑动的瀑布流中，无法提前对即 > 将要显示的图片进行下载，导致滑动白块较多。不同场景下，性能问题会有不同的表现，建议将网络下载部分与Image的显示剥离，可提前下载或者异步下载。 > > - src由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载的图片内容，不进行清除或重置操作。 > > - 当Image组件入参为[PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_类型时，只有当PixelMap对象发生变化（即指向一个新的PixelMap实例）， > Image组件才能感知到数据的变化。仅修改PixelMap对象的内容（如像素值）而不更换对象引用，无法触发数据变化的感知。 > > - Image组件入参为Base64字符串时，Base64字符串通用格式为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，其中subtype为类型声明，Base64 > EncodedData为数据对应的base64编码，其他为固定字符串。例如：png图像对应的入参为\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。 > > 1. image/subType用于声明数据内容的类型。从API版本26.0.0开始，Image组件接受任意\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_格式的Base64字符串，具体图片类 > 型由系统多媒体能力根据实际数据内容识别，无需枚举所有支持的MIME类型。对于API版本26.0.0之前版本，Image组件不会强制校验声明的类型与Base64解码后的实际图片格式是否完全一致。在部分场景下，即使声明的类型与真实 > 格式不一致，图片仍可能正常显示。为避免未来行为变化或未知问题，建议始终保持类型与实际图片格式一致。 > > 2. Image组件从API版本26.0.0开始支持通过\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_的通配写法，对于API版本26.0.0之前版本，Image组件不支持 > \_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_的通配写法，subType必须显式声明具体的图片类型。 > > 3. Image组件从API版本26.0.0开始支持通过Base64加载SVG图片，对于API版本26.0.0之前版本，Image组件不支持通过Base64字符串形式加载SVG图片。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor): ImageAttribute--><!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 \_\_\_MD\_LINK\_USD\_1\_\_\_。 \_\_\_HTML\_TAG\_USD\_8\_\_\_1. PixelMap格式为像素图，常用于图片编辑的场景。 \_\_\_HTML\_TAG\_USD\_9\_\_\_2. ResourceStr包含Resource和string格式。 \_\_\_HTML\_TAG\_USD\_10\_\_\_string格式可用于加载网络图片和本地图片。当 \_\_\_MD\_LINK\_USD\_2\_\_\_时，不支持跨包/跨模块调用该 Image组件，建议使用Resource格式来管理需全局使用的图片资源。 \_\_\_HTML\_TAG\_USD\_11\_\_\_从DevEco Studio 6.0.0 Beta2版本开始，新建工程或模块时，默认创建的模块不会对非resource目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中 buildOption > resOptions > copyCodeResource > enable 设置为true。 \_\_\_HTML\_TAG\_USD\_12\_\_\_- 支持\_\_\_INLINE\_CODE\_USD\_0\_\_\_字符串。 \_\_\_HTML\_TAG\_USD\_13\_\_\_- 传入的字符串为https网络图片地址时，建议参考 \_\_\_MD\_LINK\_USD\_3\_\_\_。 \_\_\_HTML\_TAG\_USD\_14\_\_\_- 支持file://路径前缀的字符串，应用沙箱URI：file://\_\_\_HTML\_TAG\_USD\_15\_\_\_/\_\_\_HTML\_TAG\_USD\_16\_\_\_。应用沙箱路径URI构造可参考 [constructor]\_\_\_JSDOC\_LINK\_USD\_5\_\_\_。沙箱路径需要使用 [fileUri.getUriFromPath(path)]\_\_\_JSDOC\_LINK\_USD\_6\_\_\_方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包 路径下的文件有可读权限。 \_\_\_HTML\_TAG\_USD\_17\_\_\_Resource格式可以跨包/跨模块访问资源文件，是访问本地图片的推荐方式，具体示例参考 \_\_\_MD\_LINK\_USD\_4\_\_\_。\_\_\_HTML\_TAG\_USD\_18\_\_\_3. 当传入资源id或name为普通图片 时，生成DrawableDescriptor对象。传入 [AnimatedDrawableDescriptor]\_\_\_JSDOC\_LINK\_USD\_7\_\_\_类型可播放PixelMap数组动画。 \_\_\_HTML\_TAG\_USD\_19\_\_\_**说明：**\_\_\_HTML\_TAG\_USD\_20\_\_\_- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。\_\_\_HTML\_TAG\_USD\_21\_\_\_- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

src新增[ImageContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型，可指定对应的图形内容。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent): ImageAttribute--><!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 \_\_\_MD\_LINK\_USD\_0\_\_\_。 \_\_\_HTML\_TAG\_USD\_3\_\_\_PixelMap、ResourceStr和DrawableDescriptor的使用请参考 \_\_\_MD\_LINK\_USD\_1\_\_\_的src参数说明。 \_\_\_HTML\_TAG\_USD\_4\_\_\_ 传入[ImageContent]\_\_\_JSDOC\_LINK\_USD\_2\_\_\_类型，指定图像内容。 \_\_\_HTML\_TAG\_USD\_5\_\_\_**说明：**\_\_\_HTML\_TAG\_USD\_6\_\_\_- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。\_\_\_HTML\_TAG\_USD\_7\_\_\_- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string)
```

获取图片，支持通过reloadKey参数触发图片重新加载。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string): ImageAttribute--><!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent | 是 |  |
| reloadKey | string | 否 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions)
```

Image新增[ImageAIOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_参数，为组件设置AI分析选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions): ImageAttribute--><!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 \_\_\_MD\_LINK\_USD\_0\_\_\_。 \_\_\_HTML\_TAG\_USD\_2\_\_\_PixelMap、ResourceStr和DrawableDescriptor的使用请参考 \_\_\_MD\_LINK\_USD\_1\_\_\_的src参数说明。 \_\_\_HTML\_TAG\_USD\_3\_\_\_**说明：**\_\_\_HTML\_TAG\_USD\_4\_\_\_- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。\_\_\_HTML\_TAG\_USD\_5\_\_\_- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor,
      imageAIOptions?: ImageAIOptions, reloadKey?: string)
```

获取图片，支持通过[ImageAIOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_参数设置AI分析选项。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor,      imageAIOptions?: ImageAIOptions, reloadKey?: string): ImageAttribute--><!--Device-ImageInterface-(src: PixelMap | ResourceStr | DrawableDescriptor,      imageAIOptions?: ImageAIOptions, reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor | 是 |  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| reloadKey | string | 否 |  |

## 汇总

