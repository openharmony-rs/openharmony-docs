# VideoOptions

定义Video的具体配置参数。

**起始版本：** 7

<!--Device-unnamed-declare interface VideoOptions--><!--Device-unnamed-declare interface VideoOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: VideoController
```

设置视频控制器，可以控制视频的播放状态。

**类型：** VideoController

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-controller?: VideoController--><!--Device-VideoOptions-controller?: VideoController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controllerAsync

```TypeScript
controllerAsync?: VideoControllerAsync
```

controllerAsync of video.

**类型：** VideoControllerAsync

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-controllerAsync?: VideoControllerAsync--><!--Device-VideoOptions-controllerAsync?: VideoControllerAsync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentProgressRate

```TypeScript
currentProgressRate?: number | string | PlaybackSpeed
```

视频播放倍速。

**说明：**

number格式取值仅支持：0.75，1.0，1.25，1.75，2.0。从API version 22开始，新增支持取值0.5，1.5，3，0.25和0.125。

string格式支持number格式取值的字符串形式："0.75"，"1.0"，"1.25"，"1.75"，"2.0"。从API version 22开始，新增支持取值"0.5"，"1.5"，"3"，"0.25"和"0.125"。

除此之外的取值，比如"abc"或"1.5+1.5"会按照异常值处理。

默认值：1.0 | PlaybackSpeed.Speed_Forward_1_00_X

异常值：按默认值处理。

**类型：** number \| string \| PlaybackSpeed

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-currentProgressRate?: number | string | PlaybackSpeed--><!--Device-VideoOptions-currentProgressRate?: number | string | PlaybackSpeed-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageAIOptions

```TypeScript
imageAIOptions?: ImageAIOptions
```

设置图像AI分析选项，可配置分析类型或绑定一个分析控制器。

**类型：** ImageAIOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-imageAIOptions?: ImageAIOptions--><!--Device-VideoOptions-imageAIOptions?: ImageAIOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## posterOptions

```TypeScript
posterOptions?: PosterOptions
```

设置视频播放的首帧送显选项，可以控制视频是否支持首帧送显。

**类型：** PosterOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-posterOptions?: PosterOptions--><!--Device-VideoOptions-posterOptions?: PosterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewUri

```TypeScript
previewUri?: string | PixelMap | Resource
```

视频未播放时的预览图片路径，默认不显示图片。

string格式可用于加载本地图片和网络图片，

- 支持网络图片地址。  
- 支持相对路径引用本地图片，例如：previewUri: “common/test.jpg”。当使用相对路径引用本地图片时，不支持跨包/跨模块调用。  
- 支持file://路径前缀的字符串，即应用沙箱URI（见[uriOrPath](@ohos.file.fileuri:fileUri.FileUri#constructor)）：file://<bundleName  
>/<sandboxPath>。用于读取应用沙箱路径内的资源。需要保证目录包路径下的文件有可读权限。

Resource格式可以跨包/跨模块访问资源文件。

- 支持rawfile文件下的资源，即通过$rawfile引用图片。  
- 支持通过$r引用系统资源或者应用资源中的图片。

默认值：空字符串

异常值：按默认值处理。

**类型：** string \| PixelMap \| Resource

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-previewUri?: string | PixelMap | Resource--><!--Device-VideoOptions-previewUri?: string | PixelMap | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src?: string | Resource
```

视频的数据源，支持本地视频和网络视频。

Resource格式可以跨包/跨模块访问资源文件，常用于访问本地视频。

- 仅支持rawfile文件下的资源，即通过$rawfile引用视频文件。

string格式可用于加载网络视频和本地视频，常用于加载网络视频。

- 支持网络视频地址，网络视频地址支持的格式见[流媒体支持的格式](docroot://media/media/streaming-media-playback-development-guide.md#流媒体支持的格式)。  
- 支持file://路径前缀的字符串，即应用沙箱URI（见[uriOrPath](@ohos.file.fileuri:fileUri.FileUri#constructor)）：file://<bundleName  
>/<sandboxPath>。用于读取应用沙箱路径内的资源。需要保证目录包路径下的文件有可读权限。

默认值：空字符串

异常值：按默认值处理。

**说明：**

视频支持的格式是：mp4、mkv、TS。

**类型：** string \| Resource

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOptions-src?: string | Resource--><!--Device-VideoOptions-src?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

