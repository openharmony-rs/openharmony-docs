# DownloadError

预下载错误回调的返回信息。

**起始版本：** 23

<!--Device-cacheDownload-interface DownloadError--><!--Device-cacheDownload-interface DownloadError-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## errorCode

```TypeScript
readonly errorCode: ErrorCode
```

预下载错误回调返回的特定错误类型。

**类型：** ErrorCode

**起始版本：** 23

<!--Device-DownloadError-readonly errorCode: ErrorCode--><!--Device-DownloadError-readonly errorCode: ErrorCode-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## message

```TypeScript
readonly message: string
```

返回[通用错误码](docroot://reference/errorcode-universal.md)或[HTTP错误码](docroot://reference/apis-network-kit/errorcode-net-http.md)。

**类型：** string

**起始版本：** 23

<!--Device-DownloadError-readonly message: string--><!--Device-DownloadError-readonly message: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

