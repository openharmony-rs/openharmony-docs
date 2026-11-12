# OH_UDMF_VirtualFileCallbacks

```c
typedef struct OH_UDMF_VirtualFileCallbacks {...} OH_UDMF_VirtualFileCallbacks
```

## 概述

描述用于提供虚拟文件元数据和内容的回调。<br> <code>structSize</code>必须设置为<code>sizeof(OH_UDMF_VirtualFileCallbacks)</code>。 <code>onRead</code>为必选回调，<code>onStat</code>和<code>onCancel</code>为可选回调；所有文件必须预先声明大小。 不需要取消通知时，将<code>onCancel</code>设置为nullptr。 不同线程可能并发调用回调，回调不得无限期阻塞。

<!--Device-struct OH_UDMF_VirtualFileCallbacks {...}--><!--Device-struct OH_UDMF_VirtualFileCallbacks {...}-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**相关模块：** [UDMF](capi-arkdata-udmf.md)

**所在头文件：** [uds.h](capi-uds-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小。<br>**起始版本：** 26.1.0 |
| [OH_UDMF_VirtualFileOnStat](capi-uds-h.md#oh_udmf_virtualfileonstat) onStat | 可选的元数据回调。<br>**起始版本：** 26.1.0 |
| [OH_UDMF_VirtualFileOnRead](capi-uds-h.md#oh_udmf_virtualfileonread) onRead | 必选的内容读取回调。<br>**起始版本：** 26.1.0 |
| [OH_UDMF_VirtualFileOnCancel](capi-uds-h.md#oh_udmf_virtualfileoncancel) onCancel | 可选的取消回调。为nullptr时，取消操作成功，不通知提供方。<br>**起始版本：** 26.1.0 |


