# VirtualFileInfo

```TypeScript
interface VirtualFileInfo
```

定义虚拟文件系统的根节点，以及拖拽落入成功后 UDMF 用于提供数据的回调。回调状态仅保留在起拖方进程中，不会通过落入方的数据获取操作返回。

**起始版本：** 26.1.0

<!--Device-uniformDataStruct-interface VirtualFileInfo--><!--Device-uniformDataStruct-interface VirtualFileInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## onCancel

```TypeScript
onCancel?: VirtualFileOnCancel
```

可选的取消回调。未设置时，取消操作成功，不向提供方发送回调通知。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileInfo-onCancel?: VirtualFileOnCancel--><!--Device-VirtualFileInfo-onCancel?: VirtualFileOnCancel-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## onRead

```TypeScript
onRead: VirtualFileOnRead
```

按需读取文件内容的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileInfo-onRead: VirtualFileOnRead--><!--Device-VirtualFileInfo-onRead: VirtualFileOnRead-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## onStat

```TypeScript
onStat?: VirtualFileOnStat
```

可选的文件元数据回调，不能替代必填的文件大小。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileInfo-onStat?: VirtualFileOnStat--><!--Device-VirtualFileInfo-onStat?: VirtualFileOnStat-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## itemInfo

```TypeScript
itemInfo: VirtualItemType
```

作为根节点的虚拟文件或目录。

**类型：** [VirtualItemType](arkts-arkdata-uniformdatastruct-virtualitemtype-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileInfo-itemInfo: VirtualItemType--><!--Device-VirtualFileInfo-itemInfo: VirtualItemType-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
