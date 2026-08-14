# WatchEventListener

```TypeScript
export type WatchEventListener = (event: WatchEvent) => void
```

事件监听类，当监听的文件或目录发生变动事件时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export type WatchEventListener = (event: WatchEvent) => void--><!--Device-unnamed-export type WatchEventListener = (event: WatchEvent) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [WatchEvent](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-watchevent-i.md) | 是 | 回调的事件类。 |

