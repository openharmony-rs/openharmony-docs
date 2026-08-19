# CloudMediaDownloadType（系统接口）

枚举，表示云端媒体资产的下载方式。

**起始版本：** 23

<!--Device-photoAccessHelper-enum CloudMediaDownloadType--><!--Device-photoAccessHelper-enum CloudMediaDownloadType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DOWNLOAD_FORCE

```TypeScript
DOWNLOAD_FORCE = 0
```

高优先级下载，无需进入息屏充电模式。

**起始版本：** 23

<!--Device-CloudMediaDownloadType-DOWNLOAD_FORCE = 0--><!--Device-CloudMediaDownloadType-DOWNLOAD_FORCE = 0-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## DOWNLOAD_GENTLE

```TypeScript
DOWNLOAD_GENTLE = 1
```

低优先级下载，需要进入息屏充电模式。

**起始版本：** 23

<!--Device-CloudMediaDownloadType-DOWNLOAD_GENTLE = 1--><!--Device-CloudMediaDownloadType-DOWNLOAD_GENTLE = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

