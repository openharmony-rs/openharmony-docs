# DownloadFailCallback

```TypeScript
export type DownloadFailCallback = (err: int) => void
```

The callback function for the download fail event. <br>The value should be an integer.

**起始版本：** 23

<!--Device-request-export type DownloadFailCallback = (err: int) => void--><!--Device-request-export type DownloadFailCallback = (err: int) => void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | int | 是 | the error code for download task. |

