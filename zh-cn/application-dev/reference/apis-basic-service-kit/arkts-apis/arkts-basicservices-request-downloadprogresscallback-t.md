# DownloadProgressCallback

```TypeScript
export type DownloadProgressCallback = (receivedSize: long, totalSize: long) => void
```

The callback function for the download progress event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-request-export type DownloadProgressCallback = (receivedSize: long, totalSize: long) => void--><!--Device-request-export type DownloadProgressCallback = (receivedSize: long, totalSize: long) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| receivedSize | long | 是 | the length of downloaded data, in bytes. |
| totalSize | long | 是 | the length of data expected to be downloaded, in bytes. |

