# MediaSourceLoader

Defines a media data loader, which needs to be implemented by applications.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-interface MediaSourceLoader--><!--Device-unnamed-interface MediaSourceLoader-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## close

```TypeScript
close: SourceCloseCallback
```

Callback function is implemented by application, which is used to handle resource close request.

**类型：** [SourceCloseCallback](arkts-media-sourceclosecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaSourceLoader-close: SourceCloseCallback--><!--Device-MediaSourceLoader-close: SourceCloseCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## open

```TypeScript
open: SourceOpenCallback
```

Callback function is implemented by application, which is used to handle resource opening requests.

**类型：** [SourceOpenCallback](arkts-media-sourceopencallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaSourceLoader-open: SourceOpenCallback--><!--Device-MediaSourceLoader-open: SourceOpenCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## read

```TypeScript
read: SourceReadCallback
```

Callback function is implemented by application, which is used to handle resource read requests.

**类型：** [SourceReadCallback](arkts-media-sourcereadcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaSourceLoader-read: SourceReadCallback--><!--Device-MediaSourceLoader-read: SourceReadCallback-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

