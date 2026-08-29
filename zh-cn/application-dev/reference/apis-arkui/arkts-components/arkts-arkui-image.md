# Image

Image为图片组件，常用于在应用中显示图片。Image支持加载[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)、 [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)和[DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md)类型的数据源，支持png、jpg、jpeg、bmp、svg、webp、gif 、heif和tiff类型的图片格式，不支持apng和svga格式。
> **说明：** > > - 从API version 23开始，图片类型新增支持tiff格式。 > > - 该组件从API版本26.0.0开始支持WithTheme。 > > - 使用快捷组合键对Image组件复制时，Image组件必须处于获焦状态，如何获焦请参考[设置组件是否可获焦](../../../ui/arkts-common-events-focus-event.md#设置组件是否可获焦)。 > Image组件默认不获焦，需将focusable属性设置为true，即可使用Tab键将焦点切换到组件上，再将 > [focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch)属性设置为true，即可实现点击获焦。 > > - 图片格式支持SVG图源，SVG标签文档请参考SVG标签说明。 > > - 动图的播放依赖于Image节点的可见性变化，其默认行为是不播放的。当节点可见时，通过回调启动动画，当节点不可见时，停止动画。可见性状态的判断是通过 > [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) > 事件触发的，当可见阈值ratios大于0时，表明Image处于可见状态。 > > - Image组件播放GIF动图时，帧时长取自GIF文件中各帧的delay time字段。当某帧的时长值小于等于0时，系统会将其修正为100ms；当某帧的时长值大于0时，系统直接使用该原始值，不做最小帧时长限制。
需要权限
使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。
子组件
无

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```

通过图片数据源获取图片，用于后续渲染展示。Image组件加载图片失败或图片尺寸为0时，图片组件大小自动为0，不跟随父组件的布局约束。Image组件默认按照居中裁剪，例如组件宽高设置相同，原图长宽不等，此时按照中间区域进行裁剪。Image加载成功且组件不设置宽高时，其显示大小自适应父组件。

> **说明：**
> 
> - Image直接传入URL可能会带来的潜在性能问题，例如：(1) 大图加载时无法提前下载，白块显示的时间较长；(2) 小图设置同步加载，在弱网环境下，可能会阻塞UI线程造成冻屏问题；(3) 在快速滑动的瀑布流中，无法提前对即
> 将要显示的图片进行下载，导致滑动白块较多。不同场景下，性能问题会有不同的表现，建议将网络下载部分与Image的显示剥离，可提前下载或者异步下载。
> 
> - src由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载的图片内容，不进行清除或重置操作。
> 
> - 当Image组件入参为[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)类型时，只有当PixelMap对象发生变化（即指向一个新的PixelMap实例），
> Image组件才能感知到数据的变化。仅修改PixelMap对象的内容（如像素值）而不更换对象引用，无法触发数据变化的感知。
> 
> - Image组件入参为Base64字符串时，Base64字符串通用格式为`data:image/subtype;base64,Base64EncodedData`，其中subtype为类型声明，Base64
> EncodedData为数据对应的base64编码，其他为固定字符串。例如：png图像对应的入参为`data:image/png;base64,iVBORw0KGgo...`。
> 
> 1. image/subType用于声明数据内容的类型。从API版本26.0.0开始，Image组件接受任意`data:image/xxx;base64,Base64EncodedData`格式的Base64字符串，具体图片类
> 型由系统多媒体能力根据实际数据内容识别，无需枚举所有支持的MIME类型。对于API版本26.0.0之前版本，Image组件不会强制校验声明的类型与Base64解码后的实际图片格式是否完全一致。在部分场景下，即使声明的类型与真实
> 格式不一致，图片仍可能正常显示。为避免未来行为变化或未知问题，建议始终保持类型与实际图片格式一致。
> 
> 2. Image组件从API版本26.0.0开始支持通过`data:image/*;base64,Base64EncodedData`的通配写法，对于API版本26.0.0之前版本，Image组件不支持
> `data:image/*;base64,Base64EncodedData`的通配写法，subType必须显式声明具体的图片类型。
> 
> 3. Image组件从API版本26.0.0开始支持通过Base64加载SVG图片，对于API版本26.0.0之前版本，Image组件不支持通过Base64字符串形式加载SVG图片。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 [加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。  1. PixelMap格式为像素图，常用于图片编辑的场景。  2. ResourceStr包含Resource和string格式。  string格式可用于加载网络图片和本地图片。当 使用相对路径显示图片时，不支持跨包/跨模块调用该 Image组件，建议使用Resource格式来管理需全局使用的图片资源。  从DevEco Studio 6.0.0 Beta2版本开始，新建工程或模块时，默认创建的模块不会对非resource目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中 buildOption > resOptions > copyCodeResource > enable 设置为true。  - 支持`Base64`字符串。  - 传入的字符串为https网络图片地址时，建议参考 示例2（下载与显示静态网络图片）。  - 支持file://路径前缀的字符串，应用沙箱URI：file://\<bundleName>/\<sandboxPath>。应用沙箱路径URI构造可参考 [constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor)。沙箱路径需要使用 [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md)方法将路径转换为应用沙箱URI，然后传入显示。同时需要保证目录包 路径下的文件有可读权限。  Resource格式可以跨包/跨模块访问资源文件，是访问本地图片的推荐方式，具体示例参考 [访问跨HAP/HSP包资源](../../../quick-start/resource-categories-and-access.md#访问跨haphsp包资源)。 3. 当传入资源id或name为普通图片 时，生成DrawableDescriptor对象。传入 [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)类型可播放PixelMap数组动画。  **说明：** - ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。 - ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

src新增[ImageContent](arkts-arkui-imagecontent-e.md)类型，可指定对应的图形内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) \| [ImageContent](arkts-arkui-imagecontent-e.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 [加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。  PixelMap、ResourceStr和DrawableDescriptor的使用请参考 Image的src参数说明。   传入[ImageContent](arkts-arkui-imagecontent-e.md)类型，指定图像内容。  **说明：** - ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。 - ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string)
```

获取图片，支持通过reloadKey参数触发图片重新加载。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) \| [ImageContent](arkts-arkui-imagecontent-e.md) | 是 |  |
| reloadKey | string | 否 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions)
```

Image新增[ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)参数，为组件设置AI分析选项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 | 图片的数据源，支持本地图片和网络图片，引用方式请参考 [加载图片资源](../../../ui/arkts-graphics-display.md#加载图片资源)。  PixelMap、ResourceStr和DrawableDescriptor的使用请参考 Image的src参数说明。  **说明：** - ArkTS卡片上支持gif图片格式动效，但仅在显示时播放一次。 - ArkTS卡片上不支持http://等网络相关路径前缀和file://路径前缀的字符串。 |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 是 | 给组件设置一个AI分析选项，通过此项可配置分析类型或绑定一个分析控制器。 |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor,
      imageAIOptions?: ImageAIOptions, reloadKey?: string)
```

获取图片，支持通过[ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md)参数设置AI分析选项。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 是 |  |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | 否 |  |
| reloadKey | string | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageAlt](arkts-arkui-imagealt-i.md) | 设置图片占位图。 |
| [ImageError](arkts-arkui-imageerror-i.md) | 图片加载异常时触发回调的返回对象。当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时该事件不触发。 |
| [ImageSourceSize](arkts-arkui-imagesourcesize-i.md) | 图片解码尺寸。 |
| [ResizableOptions](arkts-arkui-resizableoptions-i.md) | 图像拉伸时可调整大小的图像选项。 
**图1** 设置EdgeWidths效果图 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BusinessError](arkts-arkui-businesserror-t.md) | 图片加载异常返回的错误信息。以下是错误信息的详细介绍：ImageError的error属性为错误信息对象，其中code为错误码，message为错误信息。 |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 作为Image组件的入参对象。 |
| [DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md) | 颜色滤波器对象。 |
| [DrawingLattice](arkts-arkui-drawinglattice-t.md) | 将图片按照矩形网格进行划分。 |
| [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | 图片加载异常时触发此回调。当组件的参数类型为[AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md)时该事件不触发。 |
| [ImageMatrix](arkts-arkui-imagematrix-t.md) | 当前的矩阵对象。 |
| [RequestDownloadInfo](arkts-arkui-requestdownloadinfo-t.md) | 用于描述网络图片加载失败或异常时的下载信息。该对象包含本次下载任务的资源信息、网络信息以及性能统计信息，可用于定位加载异常的具体原因。 |
| ResolutionQuality | 分辨率质量等级类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DynamicRangeMode](arkts-arkui-dynamicrangemode-e.md) | 期望展示的图像动态范围。 |
| [ImageContent](arkts-arkui-imagecontent-e.md) | 指定图像内容。 |
| [ImageInterpolation](arkts-arkui-imageinterpolation-e.md) | 图片的渲染模式。 |
| [ImageRenderMode](arkts-arkui-imagerendermode-e.md) | 图片的渲染模式。 |
| [ImageRotateOrientation](arkts-arkui-imagerotateorientation-e.md) | 期望的图像内容显示方向。 |

## 示例

该示例通过传入Resource资源，加载png、gif、svg和jpg等基本类型的图片。

```TypeScript
@Entry
@Component
struct ImageExample1 {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // 加载png格式图片
          // $r('app.media.ic_camera_master_ai_leaf')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.ic_camera_master_ai_leaf'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // 加载gif格式图片
          // $r('app.media.loading')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
        Row() {
          // 加载svg格式图片
          // $r('app.media.ic_camera_master_ai_clouded')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.ic_camera_master_ai_clouded'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // 加载jpg格式图片
          // $r('app.media.ic_public_favor_filled')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.ic_public_favor_filled'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample2 {
  @State pixelMapImg: PixelMap | undefined = undefined;

  aboutToAppear() {
    this.requestImageUrl('https://www.example.com/xxx.png'); // 请填写一个具体的网络图片地址
  }

  requestImageUrl(url: string) {
    http.createHttp().request(url, (error: BusinessError, data: http.HttpResponse) => {
      if (error) {
        console.error(`request image failed: url: ${url}, code: ${error.code}, message: ${error.message}`);
      } else {
        let imgData: ArrayBuffer = data.result as ArrayBuffer;
        console.info(`request image success, size: ${imgData.byteLength}`);
        let imgSource: image.ImageSource = image.createImageSource(imgData);
        class sizeTmp {
          height: number = 100;
          width: number = 100;
        }
        let options: Record<string, number | boolean | sizeTmp> = {
          'alphaType': 0,
          'editable': false,
          'pixelFormat': 3,
          'scaleMode': 1,
          'size': { height: 100, width: 100 }
        }
        imgSource.createPixelMap(options).then((pixelMap: PixelMap) => {
          console.info('image createPixelMap success');
          this.pixelMapImg = pixelMap;
          imgSource.release();
        }).catch((err: BusinessError) => {
          console.error(`Failed to create pixel map. Code: ${err.code}, message: ${err.message}`);
          imgSource.release();
        })
      }
    })
  }

  build() {
    Column() {
      Image(this.pixelMapImg)
        // $r('app.media.img')需要替换为开发者所需的图像资源文件。
        .alt($r('app.media.img'))
        .objectFit(ImageFit.None)
        .width('100%')
        .height('100%')
    }
  }
}
```

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State src: string = 'https://www.example.com/xxx.gif'; // 请填写一个具体的网络图片地址。

  async aboutToAppear(): Promise<void> {
    // 提供缓存下载任务的配置选项。
    let options: cacheDownload.CacheDownloadOptions = {};
    try {
      // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。
      cacheDownload.download(this.src, options);
      console.info(`success to download the resource. `);
    } catch (err) {
      console.error(`Failed to download the resource: code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      // 若src指定的是网络图片且已成功下载并缓存，则本次显示无需重复下载。
      Image(this.src)
        .width(100)
        .height(100)
        .objectFit(ImageFit.Cover)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例为图片添加onClick和onFinish事件。

```TypeScript
@Entry
@Component
struct ImageExample3 {
  // $r('app.media.earth')需要替换为开发者所需的图像资源文件。
  private imageOne: Resource = $r('app.media.earth');
  // $r('app.media.star')需要替换为开发者所需的图像资源文件。
  private imageTwo: Resource = $r('app.media.star');
  // $r('app.media.moveStar')需要替换为开发者所需的图像资源文件。
  private imageThree: Resource = $r('app.media.moveStar');
  @State src: Resource = this.imageOne;
  @State src2: Resource = this.imageThree;
  build(){
    Column(){
      // 为图片添加点击事件，点击完成后加载特定图片
      Image(this.src)
        .width(100)
        .height(100)
        .onClick(() => {
          this.src = this.imageTwo;
        })

      // 当加载图片为SVG格式时
      Image(this.src2)
        .width(100)
        .height(100)
        .onFinish(() => {
          // SVG动效播放完成时加载另一张图片
          this.src2 = this.imageOne;
        })
    }.width('100%').height('100%')
  }
}
```

该示例使用enableAnalyzer接口开启图像AI分析。

```TypeScript
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample4 {
  @State imagePixelMap: image.PixelMap | undefined = undefined;
  private aiController: ImageAnalyzerController = new ImageAnalyzerController();
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  };

  async aboutToAppear() {
    // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件。
    this.imagePixelMap = await this.getPixmapFromMedia($r('app.media.app_icon'));
  }

  build() {
    Column() {
      Image(this.imagePixelMap, this.options)
        .enableAnalyzer(true)
        .width(200)
        .height(200)
        .margin({bottom:10})
      Button('getTypes', { type: ButtonType.Circle, stateEffect: false })
        .width(100)
        .height(100)
        .onClick(() => {
          this.aiController.getImageAnalyzerSupportTypes();
        })
    }
  }
  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let pixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return pixelMap;
  }
}
```

该示例通过resizable属性的slice选项，调整不同方向对图片进行拉伸。

```TypeScript
@Entry
@Component
struct Index {
  @State top: number = 10;
  @State bottom: number = 10;
  @State left: number = 10;
  @State right: number = 10;

  build() {
    Column({ space: 5 }) {
      // 原图效果
      // $r('app.media.landscape')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.landscape'))
        .width(200).height(200)
        .border({ width: 2, color: Color.Pink })
        .objectFit(ImageFit.Contain)

      // 图像拉伸效果，设置resizable属性，对图片不同方向进行拉伸
      // $r('app.media.landscape')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.landscape'))
        .resizable({
          slice: {
            // 传入数字时默认为vp单位，但在不同设备上vp单位会被解析成不同大小的px单位，可以根据需要选择传入的单位
            left: `${this.left}px`,
            right: `${this.right}px`,
            top: `${this.top}px`,
            bottom: `${this.bottom}px`
          }
        })
        .width(200)
        .height(200)
        .border({ width: 2, color: Color.Pink })
        .objectFit(ImageFit.Contain)

      Row() {
        Button('add top to ' + this.top).fontSize(10)
          .onClick(() => {
            this.top += 10;
          })
        Button('add bottom to ' + this.bottom).fontSize(10)
          .onClick(() => {
            this.bottom += 10;
          })
      }

      Row() {
        Button('add left to ' + this.left).fontSize(10)
          .onClick(() => {
            this.left += 10;
          })
        Button('add right to ' + this.right).fontSize(10)
          .onClick(() => {
            this.right += 10;
          })
      }

    }
    .justifyContent(FlexAlign.Start).width('100%').height('100%')
  }
}
```

该示例使用resizable属性的lattice选项，使用矩形网格对象对图片进行拉伸。

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct drawingLatticeTest {
  private xDivs: Array<number> = [1, 2, 200];
  private yDivs: Array<number> = [1, 2, 200];
  private fXCount: number = 3;
  private fYCount: number = 3;
  private drawingLatticeFirst: DrawingLattice =
    drawing.Lattice.createImageLattice(this.xDivs, this.yDivs, this.fXCount, this.fYCount);

  build() {
    Scroll() {
      Column({ space: 10 }) {
        Text('Original Image').fontSize(20).fontWeight(700)
        Column({ space: 10 }) {
          // $r('app.media.mountain')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.mountain'))
            .width(260).height(260)
        }.width('100%')

        Text('Resize by lattice').fontSize(20).fontWeight(700)
        Column({ space: 10 }) {
          // $r('app.media.mountain')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.mountain'))
            .objectRepeat(ImageRepeat.X)
            .width(260)
            .height(260)
            .resizable({
              lattice: this.drawingLatticeFirst
            })
        }.width('100%')
      }.width('100%')
    }
  }
}
```

该示例通过AnimatedDrawableDescriptor对象播放PixelMap数组动画。

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample {
  pixelMaps: PixelMap[] = [];
  @State options: AnimationOptions = { iterations: 1 };
  @State animated: AnimatedDrawableDescriptor | undefined = undefined;

  async aboutToAppear() {
    this.pixelMaps = await this.getPixelMaps();
    this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
  }

  build() {
    Column() {
      Row() {
        Image(this.animated)
          .width('500px').height('500px')
          .onFinish(() => {
            // 当Image组件的图片源为AnimatedDrawableDescriptor对象时，onFinish回调不会执行。
            console.info('finish');
          })
      }.height('50%')

      Row() {
        Button('once').width(100).padding(5).onClick(() => {
          this.options = { iterations: 1 };
          this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
        }).margin(5)
        Button('infinite').width(100).padding(5).onClick(() => {
          this.options = { iterations: -1 };
          this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
        }).margin(5)
      }
    }.width('50%')
  }

  private async getPixmapListFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let createPixelMap: image.PixelMap[] = await imageSource.createPixelMapList({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return createPixelMap;
  }

  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let pixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return pixelMap;
  }

  private async getPixelMaps() {
    // $r('app.media.mountain')需要替换为开发者所需的图像资源文件。
    let myPixelMaps: PixelMap[] = await this.getPixmapListFromMedia($r('app.media.mountain')); // 添加图片
    // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.sky')));
    // $r('app.media.clouds')需要替换为开发者所需的图像资源文件。
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.clouds')));
    // $r('app.media.landscape')需要替换为开发者所需的图像资源文件。
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.landscape')));
    return myPixelMaps;
  }
}
```

该示例通过colorFilter属性实现了给图像设置颜色滤镜效果。

```TypeScript
import { drawing, common2D } from '@kit.ArkGraphics2D';

@Entry
@Component
struct ImageExample3 {
  // 当加载图片为svg格式时
  // $r('app.media.svg1')需要替换为开发者所需的图像资源文件。
  private imageOne: Resource = $r('app.media.svg1');
  // $r('app.media.1')需要替换为开发者所需的图像资源文件。
  private imageTwo: Resource = $r('app.media.1');
  @State src: Resource = this.imageOne;
  @State src2: Resource = this.imageTwo;
  private colorFilterMatrix: number[] = [1, 0, 0, 0, 0.5,
                                         0, 1, 0, 0, 0,
                                         0, 0, 1, 0, 0,
                                         0, 0, 0, 1, 0];
  private color: common2D.Color = {
    alpha: 255,
    red: 255,
    green: 0,
    blue: 0
  };
  @State drawingColorFilterFirst: ColorFilter | undefined = undefined;
  @State drawingColorFilterSecond: ColorFilter | undefined = undefined;
  @State drawingColorFilterThird: ColorFilter | undefined = undefined;

  build() {
    Column() {
      Image(this.src)
        .width(100)
        .height(100)
        .colorFilter(this.drawingColorFilterFirst)
        .onClick(()=>{
          this.drawingColorFilterFirst =
            drawing.ColorFilter.createBlendModeColorFilter(this.color, drawing.BlendMode.SRC_IN);
        })

      Image(this.src2)
        .width(100)
        .height(100)
        .colorFilter(this.drawingColorFilterSecond)
        .onClick(()=>{
          this.drawingColorFilterSecond = new ColorFilter(this.colorFilterMatrix);
        })

      // 当加载图片为svg格式时
      // $r('app.media.svg2')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svg2'))
        .width(110)
        .height(110)
        .margin(15)
        .colorFilter(this.drawingColorFilterThird)
        .onClick(()=>{
          this.drawingColorFilterThird =
            drawing.ColorFilter.createBlendModeColorFilter(this.color, drawing.BlendMode.SRC_IN);
        })
    }
  }
}
```

该示例通过objectFit属性为图像设置填充效果。

```TypeScript
@Entry
@Component
struct ImageExample{
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // 加载png格式图片
          // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.sky'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.TOP_START)
          // 加载gif格式图片
          // $r('app.media.loading')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.BOTTOM_START)
        }
        Row() {
          // 加载svg格式图片
          // $r('app.media.svg')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.svg'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.TOP_END)
          // 加载jpg格式图片
          // $r('app.media.jpg')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.jpg'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.CENTER)
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

该示例展示了ResourceStr类型与[ImageContent](arkts-arkui-imagecontent-e.md)类型作为数据源的显示图片效果。

```TypeScript
@Entry
@Component
struct ImageContentExample {
  @State imageSrcIndex: number = 0;
  // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件。
  @State imageSrcList: (ResourceStr | ImageContent)[] = [$r('app.media.app_icon'), ImageContent.EMPTY];

  build() {
    Column({ space: 10 }) {
      Image(this.imageSrcList[this.imageSrcIndex])
        .width(100)
        .height(100)
      Button('点击切换Image的src', { type: ButtonType.Capsule, stateEffect: false })
        .height(50)
        .onClick(() => {
          this.imageSrcIndex = (this.imageSrcIndex + 1) % this.imageSrcList.length;
        })
    }.width('100%')
    .padding(20)
  }
}
```

该示例通过privacySensitive属性展示了如何配置隐私隐藏，效果展示需要卡片框架支持。

```TypeScript
@Entry
@Component
struct ImageExample {
  build() {
    Column({ space: 10 }) {
      // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
        .margin({top :30})
        .privacySensitive(true)
    }
    .alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

该示例通过linearGradient接口和animateTo()接口实现了给图片设置扫光效果。

```TypeScript
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample11 {
  private curve = curves.cubicBezierCurve(0.33, 0, 0.67, 1);
  @State moveImg: string[] = ['imageScanEffect'];
  @State moveImgVisible: Visibility = Visibility.Visible;
  @State durationTime: number = 1500;
  @State iterationsTimes: number = -1;
  @State private opacityValue: number = 0.5;
  @State imageWidth: number = 450;
  @State visible: Visibility = Visibility.Hidden;
  @State stackBackgroundColor: string = '#E1E4E9';
  @State linePositionX: number = 0 - this.imageWidth;
  @State linePositionY: number = 0;
  @State imgResource: Resource | undefined = undefined;

  startupAnimate() {
    this.moveImg.pop();
    this.moveImg.push('imageScanEffect');
    setTimeout(() => {
      // $r('app.media.img')需要替换为开发者所需的图像资源文件。
      this.imgResource = $r('app.media.img');
    }, 3000);
    this.getUIContext()?.animateTo({
      duration: this.durationTime,
      curve: this.curve,
      tempo: 1,
      iterations: this.iterationsTimes,
      delay: 0
    }, () => {
      this.linePositionX = this.imageWidth;
    })
  }

  build() {
    Column() {
      Row() {
        Stack() {
          Image(this.imgResource)
            .width(this.imageWidth)
            .height(200)
            .objectFit(ImageFit.Contain)
            .visibility(this.visible)
            .onComplete(() => {
              this.visible = Visibility.Visible;
              this.moveImg.pop();
            })
            .onError(() =>{
              setTimeout(() => {
                this.visible = Visibility.Visible;
                this.moveImg.pop();
              }, 2600)
            })
          ForEach(this.moveImg, (item: string) => {
            Row()
              .width(this.imageWidth)
              .height(200)
              .visibility(this.moveImgVisible)
              .position({ x: this.linePositionX, y: this.linePositionY })
              .linearGradient({
                direction: GradientDirection.Right,
                repeating: false,
                colors: [[0xE1E4E9, 0], [0xFFFFFF, 0.75], [0xE1E4E9, 1]]
              })
              .opacity(this.opacityValue)
          })
        }
        .backgroundColor(this.visible ? this.stackBackgroundColor : undefined)
        .margin({top: 20, left: 20, right: 20})
        .borderRadius(20)
        .clip(true)
        .onAppear(() => {
          this.startupAnimate();
        })
      }
    }
  }
}
```

从API version 15开始，新增imageMatrix属性。

```TypeScript
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .translate({ x: -400, y: -750 })
    .scale({ x: 0.5, y: 0.5 })
    .rotate({
      x: 2,
      y: 0.5,
      z: 3,
      centerX: 10,
      centerY: 10,
      angle: -10
    })

  build() {
    Row() {
      Column({ space: 50 }) {
        Column({ space: 5 }) {
          // $r('app.media.example')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.example'))
            .border({ width:2, color: Color.Black })
            .objectFit(ImageFit.Contain)
            .width(150)
            .height(150)
          Text('图片无变换')
            .fontSize('25px')
        }
        Column({ space: 5 }) {
          // $r('app.media.example')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.example'))
            .border({ width:2, color: Color.Black })
            .objectFit(ImageFit.None)
            .translate({ x: 10, y: 10 })
            .scale({ x: 0.5, y: 0.5 })
            .width(100)
            .height(100)
          Text('Image直接变换，默认显示图源左上角。')
            .fontSize('25px')
        }
        Column({ space: 5 }) {
          // $r('app.media.example')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.example'))
            .objectFit(ImageFit.MATRIX)
            .imageMatrix(this.matrix1)
            .border({ width:2, color: Color.Black })
            .width(150)
            .height(150)
          Text('通过imageMatrix变换，调整图源位置，实现最佳呈现。')
            .fontSize('25px')
        }
      }
      .width('100%')
    }
  }
}
```

该示例通过sourceSize接口自定义图片的解码尺寸。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.sky'))
        .sourceSize({width:1393, height:1080})
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
      // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.sky'))
        .sourceSize({width:13, height:10})
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例通过renderMode接口设置图片渲染模式为黑白模式。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.sky'))
        .renderMode(ImageRenderMode.Template)
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例通过[objectRepeat](arkts-arkui-image-attribute.md#objectrepeat)接口在竖直轴上重复绘制图片。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // $r('app.media.sky')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.sky'))
        .objectRepeat(ImageRepeat.Y)
        .height('90%')
        .width('90%')
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例通过fillColor属性为SVG图片设置不同颜色的填充效果。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('不设置fillColor')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
      Text('fillColor传入ColorContent.ORIGIN')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(ColorContent.ORIGIN)
      Text('fillColor传入Color.Blue')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(Color.Blue)
      Text('fillColor传入undefined')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(undefined)
    }
    .height('100%')
    .width('100%')
  }
}
```

从API version 19开始，新增hdrBrightness属性。

```TypeScript
import { image } from '@kit.ImageKit';

const TAG = 'AceImage';

@Entry
@Component
struct Index {
  // 'img_1'需要替换为开发者所需的图像资源文件。
  @State imgUrl: string = 'img_1';
  @State bright: number = 0; // 默认亮度为0
  aboutToAppear(): void {
    // 获取资源管理器中的媒体资源
    let img = this.getUIContext().getHostContext()?.resourceManager.getMediaByNameSync(this.imgUrl);
    // 创建图片源并获取图片信息
    if (img && img.buffer) {
      let imageSource = image.createImageSource(img?.buffer.slice(0));
      let imageInfo = imageSource.getImageInfoSync();
      // 检查图片信息是否获取成功
      if (imageInfo == undefined) {
        console.error(TAG, 'Failed to obtain the image information.');
      } else {
        // 成功获取到图片信息，打印HDR状态
        console.info(TAG, 'imageInfo.isHdr:' + imageInfo.isHdr);
      }
      imageSource.release();
    } else {
      console.error(TAG, 'Failed to obtain the image buffer.');
    }
  }

  build() {
    Column() {
      // $r('app.media.img_1')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.img_1')).width('50%')
        .height('auto')
        .margin({ top: 160 })
        .hdrBrightness(this.bright) // 设置图片的HDR亮度，值由bright状态控制
      Button('图片动态提亮 0->1')
        .onClick(() => {
          // 动画过渡，切换亮度值
          this.getUIContext()?.animateTo({}, () => {
            this.bright = 1.0 - this.bright;
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

该示例通过[matchTextDirection](arkts-arkui-image-attribute.md#matchtextdirection)接口，设置手机语言为维语时图片是否显示镜像翻转显示效果。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // 图片不跟随系统语言方向
          // $r('app.media.ocean')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.ocean'))
            .width(110).height(110).margin(15)
            .matchTextDirection(false)
        }
        Row() {
          // 图片跟随系统语言方向
          // $r('app.media.ocean')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.ocean'))
            .width(110).height(110).margin(15)
            .matchTextDirection(true)
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

该示例通过orientation属性，设置图像内容的显示方向。

```TypeScript
@Entry
@Component
struct OrientationExample {
  build() {
    Column() {
      Row({ space: 25 }) {
        Column() {
          Text('AUTO')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.AUTO)
        }

        Column() {
          Text('UP')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.UP)
        }

        Column() {
          Text('RIGHT')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.RIGHT)
        }
      }

      Row({ space: 25 }) {
        Column() {
          Text('DOWN')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.DOWN)
        }

        Column() {
          Text('LEFT')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.LEFT)
        }

        Column() {
          Text('UP_MIRRORED')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.UP_MIRRORED)
        }
      }

      Row({ space: 15 }) {
        Column() {
          Text('RIGHT_MIRRORED')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.RIGHT_MIRRORED)
        }

        Column() {
          Text('DOWN_MIRRORED')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.DOWN_MIRRORED)
        }

        Column() {
          Text('LEFT_MIRRORED')
          // $r('app.media.hello')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.LEFT_MIRRORED)
        }
      }
    }
  }
}
```

该示例通过getImageProperty接口，获取图片的exif信息，再根据获取到的exif信息，通过orientation属性设置图像内容显示为正确方向。

```TypeScript
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';

@Entry
@Component
struct Example {
  @State rotateOrientation: ImageRotateOrientation = ImageRotateOrientation.UP;
  @State pixelMap: image.PixelMap | undefined = undefined;
  @State text1: string = 'The exif orientation is ';
  @State text2: string = 'Set orientation to ';

  // 根据获取到的EXIF方向信息，转换ImageRotateOrientation，使图片显示为正确的方向。
  getOrientation(orientation: string): ImageRotateOrientation {
    if (orientation == 'Top-right') {
      this.text2 = this.text2 + 'UP_MIRRORED';
      return ImageRotateOrientation.UP_MIRRORED;
    } else if (orientation == 'Bottom-right') {
      this.text2 = this.text2 + 'DOWN';
      return ImageRotateOrientation.DOWN;
    } else if (orientation == 'Bottom-left') {
      this.text2 = this.text2 + 'DOWN_MIRRORED';
      return ImageRotateOrientation.DOWN_MIRRORED;
    } else if (orientation == 'Left-top') {
      this.text2 = this.text2 + 'LEFT_MIRRORED';
      return ImageRotateOrientation.LEFT_MIRRORED;
    } else if (orientation == 'Right-top') {
      this.text2 = this.text2 + 'RIGHT';
      return ImageRotateOrientation.RIGHT;
    } else if (orientation == 'Right-bottom') {
      this.text2 = this.text2 + 'RIGHT_MIRRORED';
      return ImageRotateOrientation.RIGHT_MIRRORED;
    } else if (orientation == 'Left-bottom') {
      this.text2 = this.text2 + 'LEFT';
      return ImageRotateOrientation.LEFT;
    } else if (orientation == 'Top-left') {
      this.text2 = this.text2 + 'UP';
      return ImageRotateOrientation.UP;
    } else {
      this.text2 = this.text2 + 'UP';
      return ImageRotateOrientation.UP;
    }
  }

  async getFileBuffer(context: Context): Promise<ArrayBuffer | undefined> {
    try {
      const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
      // 传入带有EXIF信息的资源文件，获取资源文件内容，返回Uint8Array。
      // 'hello.jpg'需要替换为开发者所需的图像资源文件。
      const fileData: Uint8Array = await resourceMgr.getRawFileContent('hello.jpg');
      console.info('Successfully get RawFileContent');
      // 转为ArrayBuffer并返回。
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (error) {
      console.error('Failed to get RawFileContent');
      return undefined;
    }
  }

  aboutToAppear() {
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return;
    }
    this.getFileBuffer(context).then((buf: ArrayBuffer | undefined) => {
      let imageSource = image.createImageSource(buf);
      if (!imageSource) {
        return;
      }
      // 从图像源中读取图片的EXIF方向信息。
      imageSource.getImageProperty(image.PropertyKey.ORIENTATION).then((orientation) => {
        this.rotateOrientation = this.getOrientation(orientation);
        this.text1 = this.text1 + orientation;
        let options: image.DecodingOptions = {
          'editable': true,
          'desiredPixelFormat': image.PixelMapFormat.RGBA_8888,
        }
        imageSource.createPixelMap(options).then((pixelMap: image.PixelMap) => {
          this.pixelMap = pixelMap;
          imageSource.release();
        });
      }).catch(() => {
        imageSource.release();
      });
    })
  }

  build() {
    Column({ space: 40 }) {
      Column({ space: 10 }) {
        Text('before').fontSize(20).fontWeight(700)
        // 'hello.jpg'需要替换为开发者所需的图像资源文件。
        Image($rawfile('hello.jpg'))
          .width(100)
          .height(100)
        Text(this.text1)
      }

      Column({ space: 10 }) {
        Text('after').fontSize(20).fontWeight(700)
        Image(this.pixelMap)
          .width(100)
          .height(100)
          .orientation(this.rotateOrientation)
        Text(this.text2)
      }
    }
    .height('80%')
    .width('100%')
  }
}
```

通过按钮切换不同色域下的颜色值，动态改变SVG图片的填充颜色效果，以展示ColorMetrics类型的使用方式和显示差异。

```TypeScript
import { ColorMetrics } from '@kit.ArkUI';
@Entry
@Component
struct fillColorMetricsDemo {
  @State p3Red: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.631, 0.0392, 0.1294);
  @State sRGBRed: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.631, 0.0392, 0.1294);
  @State p3Green: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.09, 0.662 ,0.552);
  @State sRGBGreen: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.09, 0.662 ,0.552);
  @State p3Blue: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 0.290 ,0.686);
  @State sRGBBlue: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0, 0.290 ,0.686);
  @State colorArray: (Color|undefined|ColorMetrics|ColorContent)[] = [
    this.p3Red, this.sRGBRed, this.p3Green, this.sRGBGreen, this.p3Blue,
    this.sRGBBlue, ColorContent.ORIGIN, Color.Gray, undefined
  ]
  @State colorArrayStr: string[] = [
    'P3 Red', 'SRGB Red', 'P3 Green', 'SRGB Green',
    'P3 Blue', 'SRGB Blue', 'ORIGIN', 'Gray', 'undefined'
  ]
  @State arrayIdx: number = 0
  build() {
    Column() {
      Text('FillColor is ' + this.colorArrayStr[this.arrayIdx])
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.colorArray[this.arrayIdx])
      Button('ChangeFillColor')
        .onClick(()=>{
          this.arrayIdx = (this.arrayIdx + 1) % this.colorArray.length
        })
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Red')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBRed)
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Green')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBGreen)
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Blue')
      // $r('app.media.svgExample')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBBlue)
    }
  }
}
```

在当前应用的目录下预置一张名为的图片，随后使用应用沙箱路径显示该图片。

```TypeScript
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
  private getSandBoxUri(): string {
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return '';
    }
    // /data/storage/el2/base/haps/entry/files/cloud.png
    // 从应用沙箱中的文件路径获取URI
    // '/cloud.png'需要替换为开发者所需的图像资源文件。
    return fileUri.getUriFromPath(context.filesDir + '/cloud.png');
  }

  build() {
    Column() {
      Image(this.getSandBoxUri())
        .width(150)
        .height(150)
    }
    .height('100%')
    .width('100%')
  }
}
```

在工程目录同级位置创建目录，在目录下预置一张名为的图片，随后使用相对路径显示该图片。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Image('common/cloud1.png')
        .width(100)
        .height(100)
    }
    .height('100%')
    .width('100%')
  }
}
```

从API version 21开始，新增supportSvg2属性。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('supportSvg2参数设置为true')
        // $rawfile('image.svg')需要替换为开发者所需的图像资源文件。
        Image($rawfile('image.svg'))
          .width(200)
          .height(200)
          .border({ width: 2, color: 'red' })
          .supportSvg2(true)
          .margin({ bottom: 30 })
        Text('supportSvg2参数设置为false（默认值）')
        // $rawfile('image.svg')需要替换为开发者所需的图像资源文件。
        Image($rawfile('image.svg'))
          .width(200)
          .height(200)
          .border({ width: 2, color: 'red' })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

从API version 21开始，该示例演示了在点击图片切换图源时，通过contentTransition属性实现淡入淡出效果，完成图片的平滑过渡。

```TypeScript
@Entry
@Component
struct ImageExample {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  @State imageResource: Resource = $r('app.media.icon');

  build() {
    Row() {
      Column() {
        Image(this.imageResource)
          .width(200)
          .height(200)
          // 启用淡入淡出过渡效果。
          .contentTransition(ContentTransitionEffect.OPACITY)
          .onClick(() => {
            // $r('app.media.cloud1')需要替换为开发者所需的图像资源文件。
            this.imageResource = $r('app.media.cloud1')
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

该示例演示了在图片加载过程中和加载失败时，通过设置alt属性实现图片加载过程中和图片加载失败时显示指定图片

```TypeScript
@Entry
@Component
struct ImageExample {
  build() {
      Column() {
      Text('同时设置placeholder属性和error属性')
      // 设置一个错误网址来触发alt的placeholder属性和error属性。
      Image("https://www.example.com/xxx.png")
      // $r('app.media.startIcon')和$r('app.media.example')需要替换为开发者所需的图像资源文件。
        .alt({ placeholder: $r('app.media.startIcon'), error: $r('app.media.example') })
        .width(100)
        .height(100)
        .margin(20)
      Text('只设置placeholder属性')
      Image("https://www.example.com/xxx.png")
        .alt({ placeholder: $r('app.media.startIcon')})
        .width(100)
        .height(100)
        .margin(20)
      Text('只设置error属性')
      Image("https://www.example.com/xxx.png")
        .alt({error: $r('app.media.example')})
        .width(100)
        .height(100)
        .margin(20)
      }
    .width('100%')
    .height('100%')
  }
}
```

从API version 23开始，ImageError新增downloadInfo属性。

```TypeScript
@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Image('https://www.example.com/xxx.png') // 请填写一个具体的网络图片地址
        .height(100)
        .width(100)
        .onError((e)=>{
          console.error(`DownloadErrorInfo: ${JSON.stringify(e?.downloadInfo)}`)
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

从API version 23开始，新增[antialiased](arkts-arkui-image-attribute.md#antialiased)接口。

```TypeScript
@Entry
@Component
struct ImageExample {
  // $r('app.media.icon')需要替换为开发者所需的图像资源文件。
  @State imageResource: Resource = $r('app.media.icon');

  build() {
    Row() {
      Blank()
        .width(50)

      Column() {
        Blank()
          .height(20)
        Text('没有设置抗锯齿的有旋转角度的图片')
        Blank()
          .height(20)
        Image(this.imageResource)
          .width(50)
          .height(50)
          .rotate({angle: 1})

        Blank()
          .height(20)
        Text('设置了抗锯齿的有旋转角度的图片')
        Blank()
          .height(20)
        Image(this.imageResource)
          .width(50)
          .height(50)
          .rotate({angle: 1})
          .antialiased(true)
      }
    }
  }
}
```
