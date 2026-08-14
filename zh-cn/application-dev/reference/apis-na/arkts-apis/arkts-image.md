# image

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColorContent](arkts-na-image-colorcontent-c.md) | 指定颜色填充内容。 |
| [ExtendableImage](arkts-na-image-extendableimage-c.md) | 扩展图像组件定义 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageAlt](arkts-na-image-imagealt-i.md) | 设置图片占位图。 |
| [ImageCompleteEvent](arkts-na-image-imagecompleteevent-i.md) | 图片数据加载成功和解码成功时触发回调的返回对象。 当组件的参数类型为[AnimatedDrawableDescriptor] AnimatedDrawableDescriptor时该事件不触发。 |
| [ImageError](arkts-na-image-imageerror-i.md) |  |
| [ImageSourceSize](arkts-na-image-imagesourcesize-i.md) | 图片解码尺寸。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [ResizableOptions](arkts-na-image-resizableoptions-i.md) | 图像拉伸时可调整大小的图像选项。 **图1** 设置EdgeWidths效果图  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DynamicRangeMode](arkts-na-image-dynamicrangemode-e.md) |  |
| [ImageContent](arkts-na-image-imagecontent-e.md) | 指定图像内容。 |
| [ImageInterpolation](arkts-na-image-imageinterpolation-e.md) |  |
| [ImageRenderMode](arkts-na-image-imagerendermode-e.md) |  |
| [ImageRotateOrientation](arkts-na-image-imagerotateorientation-e.md) |  |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DrawingColorFilter](arkts-na-drawingcolorfilter-t.md) | type DrawingColorFilter = drawing.ColorFilter 颜色滤波器对象。 |
| [DrawingLattice](arkts-na-drawinglattice-t.md) | type DrawingLattice = drawing.Lattice 将图片按照矩形网格进行划分。 |
| [ImageErrorCallback](arkts-na-imageerrorcallback-t.md) | 图片加载异常时触发此回调。 当组件的参数类型为 AnimatedDrawableDescriptor时该事件不触发。 |
| [ImageMatrix](arkts-na-imagematrix-t.md) | type ImageMatrix = matrix4.Matrix4Transit 当前的矩阵对象。 |
| [ImageOnCompleteCallback](arkts-na-imageoncompletecallback-t.md) | 图片数据加载成功和解码成功时触发该回调。 当组件的参数类型为 AnimatedDrawableDescriptor时该事件不触发。 |
| [RequestDownloadInfo](arkts-na-requestdownloadinfo-t.md) | type RequestDownloadInfo = cacheDownload.DownloadInfo 用于描述网络图片加载失败或异常时的下载信息。该对象包含本次下载任务的资源信息、网络信息以及性能统计信息， 可用于定位加载异常的具体原因。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ResolutionQuality](arkts-na-resolutionquality-t-sys.md) | type ResolutionQuality = image.ResolutionQuality; 画质效果等级类型。 |
<!--DelEnd-->

