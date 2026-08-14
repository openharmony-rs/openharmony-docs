# DfsListeners

事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export interface DfsListeners--><!--Device-unnamed-export interface DfsListeners-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## onStatus

```TypeScript
onStatus(networkId: string, status: number): void
```

事件回调类。参数由[connectDfs](arkts-corefile-file-fs-connectdfs-f.md#connectDfs)传入。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-DfsListeners-onStatus(networkId: string, status: number): void--><!--Device-DfsListeners-onStatus(networkId: string, status: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。 |
| status | number | 是 | 分布式文件系统的状态码（以connectDfs回调onStatus的特定错误码作为入参）。触发场景为 connectDfs调用过程中出现对端设备异常，对应错误码为：- 13900046：软件造成连接中断。 |

