# DfsListenerCallback

```TypeScript
type DfsListenerCallback = (networkId: string, status: int) => void
```

DfsListener Callback function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileIo-type DfsListenerCallback = (networkId: string, status: int) => void--><!--Device-fileIo-type DfsListenerCallback = (networkId: string, status: int) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 设备的网络Id。 |
| status | int | 是 | 分布式文件系统的状态码（以connectDfs回调onStatus的特定错误码作为入参）。 触发场景为connectDfs调用过程中出现对端设备异常，对应错误码为：- 13900046：软件造成连接中断。 |

