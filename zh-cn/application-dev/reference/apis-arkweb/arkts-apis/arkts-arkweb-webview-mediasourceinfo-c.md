# MediaSourceInfo

MediaSourceInfo 是表示媒体源信息的数据类。在 Web 媒体播放场景中，MediaSourceInfo 类封装了媒体源的基本信息，帮助应用了解媒体源的类型、地址和格式，应用根据这些信息创建自定义播放器并开始播放。

**起始版本：** 12

<!--Device-webview-class MediaSourceInfo--><!--Device-webview-class MediaSourceInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## format

```TypeScript
format: string
```

媒体源格式，可能为空，需要开发者自行判断格式。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaSourceInfo-format: string--><!--Device-MediaSourceInfo-format: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## source

```TypeScript
source: string
```

媒体源地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaSourceInfo-source: string--><!--Device-MediaSourceInfo-source: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: SourceType
```

媒体源的类型。

**类型：** SourceType

**起始版本：** 12

<!--Device-MediaSourceInfo-type: SourceType--><!--Device-MediaSourceInfo-type: SourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

