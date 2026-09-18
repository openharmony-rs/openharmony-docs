# Image

Image为图片组件，常用于在应用中显示图片。Image支持加载[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)、[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)和[DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md)类型的数据源，支持png、jpg、jpeg、bmp、svg、webp、gif、heif和tiff类型的图片格式，不支持apng和svga格式。

> **说明：** > > - 从API version 23开始，图片类型新增支持tiff格式。 > > - 该组件从API版本26.0.0开始支持WithTheme。 > > - 使用快捷组合键对Image组件复制时，Image组件必须处于获焦状态，如何获焦请参考[设置组件是否可获焦](../../../ui/arkts-common-events-focus-event.md#设置组件是否可获焦)。 > Image组件默认不获焦，需将focusable属性设置为true，即可使用Tab键将焦点切换到组件上，再将 > [focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch)属性设置为true，即可实现点击获焦。 > > - 图片格式支持SVG图源，SVG标签文档请参考SVG标签说明。 > > - 动图的播放依赖于Image节点的可见性变化，其默认行为是不播放的。当节点可见时，通过回调启动动画，当节点不可见时，停止动画。可见性状态的判断是通过 > [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) > 事件触发的，当可见阈值ratios大于0时，表明Image处于可见状态。 > > - Image组件播放GIF动图时，帧时长取自GIF文件中各帧的delay time字段。当某帧的时长值小于等于0时，系统会将其修正为100ms；当某帧的时长值大于0时，系统直接使用该原始值，不做最小帧时长限制。

需要权限

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

子组件

无

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```

通过图片数据源获取图片，用于后续渲染展示。

Image组件加载图片失败或图片尺寸为0时，图片组件大小自动为0，不跟随父组件的布局约束。

Image组件默认按照居中裁剪，例如组件宽高设置相同，原图长宽不等，此时按照中间区域进行裁剪。

Image加载成功且组件不设置宽高时，其显示大小自适应父组件。

> **说明：** 
> 
> - Image直接传入URL可能会带来的潜在性能问题，例如：(1) 大图加载时无法提前下载，白块显示的时间较长；(2) 小图设置同步加载，在弱网环境下，可能会阻塞UI线程造成冻屏问题；(3) 在快速滑动的瀑布流中，无法提前对即将要显示的图片进行下载，导致滑动白块较多。不同场景下，性能问题会有不同的表现，建议将网络下载部分与Image的显示剥离，可提前下载或者异步下载。
> 
> - src由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载的图片内容，不进行清除或重置操作。
> 
> - 当Image组件入参为[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型时，只有当PixelMap对象发生变化（即指向一个新的PixelMap实例），Image组件才能感知到数据的变化。仅修改PixelMap对象的内容（如像素值）而不更换对象引用，无法触发数据变化的感知。
> 
> - Image组件入参为Base64字符串时，Base64字符串通用格式为`data:image/subtype;base64,Base64EncodedData`，其中subtype为类型声明，Base64EncodedData为数据对应的base64编码，其他为固定字符串。例如：png图像对应的入参为`data:image/png;base64,iVBORw0KGgo...`。
> 
> 1. image/subType用于声明数据内容的类型。从API版本26.0.0开始，Image组件接受任意`data:image/xxx;base64,Base64EncodedData`格式的Base64字符串，具体图片类型由系统多媒体能力根据实际数据内容识别，无需枚举所有支持的MIME类型。对于API版本26.0.0之前版本，Image组件不会强制校验声明的类型与Base64解码后的实际图片格式是否完全一致。在部分场景下，即使声明的类型与真实格式不一致，图片仍可能正常显示。为避免未来行为变化或未知问题，建议始终保持类型与实际图片格式一致。
> 
> 2. Image组件从API版本26.0.0开始支持通过`data:image/*;base64,Base64EncodedData`的通配写法，对于API版本26.0.0之前版本，Image组件不支持`data:image/*;base64,Base64EncodedData`的通配写法，subType必须显式声明具体的图片类型。
> 
> 3. Image组件从API版本26.0.0开始支持通过Base64加载SVG图片，对于API版本26.0.0之前版本，Image组件不支持通过Base64字符串形式加载SVG图片。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。<br>1. PixelMap格式为像素图，常用于图片编辑的场景。<br>2. ResourceStr包含Resource和string格式。<br>string格式可用于加载网络图片和本地图片。当使用相对路径显示图片时，不支持跨包/跨模块调用该Image组件，建议使用Resource格式来管理需全局使用的图片资源。<br>从DevEco Studio 6.0.0 Beta2版本开始，新建工程或模块时，默认创建的模块不会对非resource目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOption &gt; resOptions &gt; copyCodeResource &gt; enable 设置为true。<br>- 支持`Base64`字符串。<br>- 传入的字符串为https网络图片地址时，建议参考示例2（下载与显示静态网络图片）。<br>- 支持file://路径前缀的字符串，应用沙箱URI：file://&lt;bundleName&gt;/&lt;sandboxPath&gt;。应用沙箱路径URI构造可参考[constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。沙箱路径需要使用[fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md)方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包路径下的文件有可读权限。<br>Resource格式可以跨包/跨模块访问资源文件，是访问本地图片的推荐方式，具体示例参考[访问跨HAP/HSP包资源](../../../quick-start/resource-categories-and-access.md#访问跨HAP/HSP包资源)。<br>3. 当传入资源id或name为普通图片时，生成DrawableDescriptor对象。传入[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)类型可播放PixelMap数组动画。<br>**说明：** <br>- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。<br>- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

src新增[ImageContent](arkts-arkui-imagecontent-e.md)类型，可指定对应的图形内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-imagecontent-e.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。<br>PixelMap、ResourceStr和DrawableDescriptor的使用请参考Image的src参数说明。<br> 传入[ImageContent](arkts-arkui-imagecontent-e.md)类型，指定图像内容。<br>**说明：** <br>- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。<br>- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string)
```

获取图片，支持通过reloadKey参数触发图片重新加载。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-imagecontent-e.md) | 是 |  |
| reloadKey | string | 否 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions)
```

Image新增[ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)参数，为组件设置AI分析选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考[加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。<br>PixelMap、ResourceStr和DrawableDescriptor的使用请参考Image的src参数说明。<br>**说明：** <br>- ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。<br>- ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor,
      imageAIOptions?: ImageAIOptions, reloadKey?: string)
```

获取图片，支持通过[ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)参数设置AI分析选项。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 |  |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 否 |  |
| reloadKey | string | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageAlt](arkts-arkui-imagealt-i.md) | 设置图片占位图。 |
| [ImageError](arkts-arkui-imageerror-i.md) | 图片加载异常时触发回调的返回对象。 |
| [ImageSourceSize](arkts-arkui-imagesourcesize-i.md) | 图片解码尺寸。 |
| [ResizableOptions](arkts-arkui-resizableoptions-i.md) | 图像拉伸时可调整大小的图像选项。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BusinessError](arkts-arkui-businesserror-t.md) | 图片加载异常返回的错误信息。 |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 作为Image组件的入参对象。 |
| [DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md) | 颜色滤波器对象。 |
| [DrawingLattice](arkts-arkui-drawinglattice-t.md) | 将图片按照矩形网格进行划分。 |
| [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | 图片加载异常时触发此回调。 |
| [ImageMatrix](arkts-arkui-imagematrix-t.md) | 当前的矩阵对象。 |
| [RequestDownloadInfo](arkts-arkui-requestdownloadinfo-t.md) | 用于描述网络图片加载失败或异常时的下载信息。该对象包含本次下载任务的资源信息、网络信息以及性能统计信息，可用于定位加载异常的具体原因。 |
| [ResolutionQuality](arkts-arkui-resolutionquality-t-sys.md) | 分辨率质量等级类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DynamicRangeMode](arkts-arkui-dynamicrangemode-e.md) | 期望展示的图像动态范围。 |
| [ImageContent](arkts-arkui-imagecontent-e.md) | 指定图像内容。 |
| [ImageInterpolation](arkts-arkui-imageinterpolation-e.md) | 图片的渲染模式。 |
| [ImageRenderMode](arkts-arkui-imagerendermode-e.md) | 图片的渲染模式。 |
| [ImageRotateOrientation](arkts-arkui-imagerotateorientation-e.md) | 期望的图像内容显示方向。 |

## 示例

```TypeScript
### 示例1（加载基本类型图片）

该示例通过传入[Resource](ts-types.md#resource)资源，加载png、gif、svg和jpg等基本类型的图片。


```

```TypeScript
### 示例2（下载与显示静态网络图片）

加载网络图片时，默认网络超时是5分钟，建议使用alt配置加载时的占位图。使用[HTTP](../../../network/http-request.md)工具包发送网络请求，接着将返回的数据解码为Image组件中的，加载gif到时，gif显示为静态图。图片开发可参考[Image Kit简介](../../../media/image/image-overview.md)。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。


```

```TypeScript
### 示例3（下载与显示网络gif图片）

该示例使用cacheDownload.download接口下载网络gif图片。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。
```

```TypeScript
### 示例4（为图片添加事件）

该示例为图片添加[onClick](ts-universal-events-click.md#onclick)和[onFinish](#onfinish)事件。


```

```TypeScript
### 示例5（开启图像AI分析）

该示例使用[enableAnalyzer](#enableanalyzer11)接口开启图像AI分析。


```

```TypeScript
### 示例6（通过slice拉伸图片）

该示例通过[resizable](#resizable11)属性的slice选项，调整不同方向对图片进行拉伸。


```

```TypeScript
### 示例7（通过lattice拉伸图片）

该示例使用[resizable](#resizable11)属性的lattice选项，使用矩形网格对象对图片进行拉伸。


```

```TypeScript
### 示例8（播放PixelMap数组动画）

该示例通过AnimatedDrawableDescriptor对象播放PixelMap数组动画。


```

```TypeScript
### 示例9（为图像设置颜色滤镜效果）

该示例通过[colorFilter](#colorfilter9)属性实现了给图像设置颜色滤镜效果。


```

```TypeScript
### 示例10（为图像设置填充效果）

该示例通过[objectFit](#objectfit)属性为图像设置填充效果。


```

```TypeScript
### 示例11（切换显示不同类型图片）

该示例展示了[ResourceStr](ts-types.md#resourcestr)类型与[ImageContent](arkts-arkui-imagecontent-e.md)类型作为数据源的显示图片效果。


```

```TypeScript
### 示例12（配置隐私隐藏）

该示例通过[privacySensitive](#privacysensitive12)属性展示了如何配置隐私隐藏，效果展示需要卡片框架支持。


```

```TypeScript
### 示例13（为图片设置扫光效果）

该示例通过[linearGradient](./ts-basic-components-datapanel.md#lineargradient10)接口和[animateTo()](../arkts-apis-uicontext-uicontext.md#animateto)接口实现了给图片设置扫光效果。


```

```TypeScript
### 示例14（为图片添加变换效果）

该示例通过[imageMatrix](#imagematrix15)和[objectFit](#objectfit)属性，为图片添加旋转和平移的效果。

从API version 15开始，新增imageMatrix属性。


```

```TypeScript
### 示例15（通过sourceSize设置图片解码尺寸）

该示例通过[sourceSize](#sourcesize)接口自定义图片的解码尺寸。


```

```TypeScript
### 示例16（通过renderMode设置图片的渲染模式）

该示例通过[renderMode](#rendermode)接口设置图片渲染模式为黑白模式。


```

```TypeScript
### 示例17（通过objectRepeat设置图片的重复样式）

该示例通过[objectRepeat](arkts-arkui-image-comp-attribute.md#objectrepeat)接口在竖直轴上重复绘制图片。


```

```TypeScript
### 示例18（设置SVG图片的填充颜色）

该示例通过[fillColor](#fillcolor15)属性为SVG图片设置不同颜色的填充效果。


```

```TypeScript
### 示例19（设置HDR图源动态提亮）

该示例通过[hdrBrightness](#hdrbrightness19)属性调整HDR图源的亮度，将hdrBrightness从0调整到1。

从API version 19开始，新增hdrBrightness属性。
```

```TypeScript
### 示例20（设置图片是否跟随系统语言方向）

该示例通过[matchTextDirection](arkts-arkui-image-comp-attribute.md#matchtextdirection)接口，设置手机语言为维语时图片是否显示镜像翻转显示效果。


```

```TypeScript
### 示例21（设置图像内容的显示方向）

该示例通过[orientation](#orientation14)属性，设置图像内容的显示方向。


```

```TypeScript
### 示例22（获取图片的exif信息并设置图像内容的显示方向）

该示例通过[getImageProperty](../../apis-image-kit/arkts-apis-image-ImageSource.md#getimageproperty)接口，获取图片的exif信息，再根据获取到的exif信息，通过[orientation](#orientation14)属性设置图像内容显示为正确方向。


```

```TypeScript
### 示例23（动态切换SVG图片的填充颜色）

通过按钮切换不同色域下的颜色值，动态改变SVG图片的填充颜色效果，以展示ColorMetrics类型的使用方式和显示差异。


```

```TypeScript
### 示例24（使用应用沙箱路径显示图片）

在当前应用的目录下预置一张名为的图片，随后使用应用沙箱路径显示该图片。


```

```TypeScript
### 示例25（使用相对路径显示图片）

在工程目录同级位置创建目录，在目录下预置一张名为的图片，随后使用相对路径显示该图片。


```

```TypeScript
### 示例26（使用supportSvg2属性时，SVG图片的显示效果）

该示例通过设置[supportSvg2](#supportsvg221)属性，使SVG标签解析能力增强功能生效。

从API version 21开始，新增supportSvg2属性。


```

```TypeScript
### 示例27（使用ContentTransition属性实现图片淡入淡出切换效果）

从API version 21开始，该示例演示了在点击图片切换图源时，通过[contentTransition](#contenttransition21)属性实现淡入淡出效果，完成图片的平滑过渡。


```

```TypeScript
### 示例28（使用alt属性设置加载过程中和加载失败时的占位图）

该示例演示了在图片加载过程中和加载失败时，通过设置[alt](#alt22)属性实现图片加载过程中和图片加载失败时显示指定图片


```

```TypeScript
### 示例29（使用onError回调监听网络图片加载异常信息）

该示例演示如何通过[onError](#onerror9)回调获取网络图片加载异常时的详细下载信息[ImageError](arkts-arkui-imageerror-i.md)。当图片加载失败时，可通过ImageError中的downloadInfo属性获取网络图片下载的详细信息，包括下载的资源信息、网络请求信息以及性能统计信息，有助于快速定位网络异常或资源错误原因。

从API version 23开始，ImageError新增downloadInfo属性。
```

```TypeScript
### 示例30（设置位图图片边缘抗锯齿）

该示例演示了如何通过设置[antialiased](arkts-arkui-image-comp-attribute.md#antialiased)接口开启位图图片边缘的抗锯齿功能。

从API version 23开始，新增[antialiased](arkts-arkui-image-comp-attribute.md#antialiased)接口。
```
