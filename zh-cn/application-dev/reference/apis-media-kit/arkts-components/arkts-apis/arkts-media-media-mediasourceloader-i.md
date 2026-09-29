# MediaSourceLoader

```TypeScript
interface MediaSourceLoader
```

用于定义媒体数据加载器，需要应用程序对其进行实现。

**起始版本：** 18

<!--Device-media-interface MediaSourceLoader--><!--Device-media-interface MediaSourceLoader-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## close

```TypeScript
close: SourceCloseCallback
```

由应用程序实现的回调函数，用于处理资源关闭请求。

**起始版本：** 18

**原子化服务API（仅ArkTS-Dyn）：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-MediaSourceLoader-close: SourceCloseCallback--><!--Device-MediaSourceLoader-close: SourceCloseCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## open

```TypeScript
open: SourceOpenCallback
```

由应用程序实现的回调函数，用于处理资源打开请求。

**起始版本：** 18

**原子化服务API（仅ArkTS-Dyn）：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-MediaSourceLoader-open: SourceOpenCallback--><!--Device-MediaSourceLoader-open: SourceOpenCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## read

```TypeScript
read: SourceReadCallback
```

由应用程序实现的回调函数，用于处理资源读取请求。

**起始版本：** 18

**原子化服务API（仅ArkTS-Dyn）：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-MediaSourceLoader-read: SourceReadCallback--><!--Device-MediaSourceLoader-read: SourceReadCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core
