# RequestOptions

请求策略。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## compatibleMode

```TypeScript
compatibleMode?: CompatibleMode
```

配置HDR视频资源转码模式，可指定配置为转码和不转码两种策略。默认为原视频资源内容模式即不转码。

**类型：** [CompatibleMode](arkts-medialibrary-photoaccesshelper-compatiblemode-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## deliveryMode

```TypeScript
deliveryMode: DeliveryMode
```

请求资源分发模式，可以指定对于该资源的请求策略，可被配置为快速模式，高质量模式，均衡模式三种策略。

**类型：** [DeliveryMode](arkts-medialibrary-photoaccesshelper-deliverymode-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## mediaAssetProgressHandler

```TypeScript
mediaAssetProgressHandler?: MediaAssetProgressHandler
```

配置HDR视频转码为SDR视频时的进度级回调。

**类型：** [MediaAssetProgressHandler](arkts-medialibrary-photoaccesshelper-mediaassetprogresshandler-i.md)

**起始版本：** 15

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
