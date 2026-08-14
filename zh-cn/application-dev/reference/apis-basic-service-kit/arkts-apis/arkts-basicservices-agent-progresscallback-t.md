# ProgressCallback

```TypeScript
export type ProgressCallback = (progress: Progress) => void
```

The callback function for the download progress event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-export type ProgressCallback = (progress: Progress) => void--><!--Device-agent-export type ProgressCallback = (progress: Progress) => void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | Progress | 是 | callback function with a `Progress` argument. |

