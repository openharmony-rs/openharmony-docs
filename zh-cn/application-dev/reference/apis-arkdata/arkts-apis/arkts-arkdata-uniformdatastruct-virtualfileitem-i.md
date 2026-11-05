# VirtualFileItem

```TypeScript
interface VirtualFileItem extends VirtualBaseItem
```

描述按需提供内容的虚拟文件。起拖时必须声明文件大小。

**继承/实现关系：** VirtualFileItem extends [VirtualBaseItem](arkts-arkdata-uniformdatastruct-virtualbaseitem-i.md)

**起始版本：** 26.1.0

<!--Device-uniformDataStruct-interface VirtualFileItem extends VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualFileItem extends VirtualBaseItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## id

```TypeScript
id: string
```

传给虚拟文件回调的文件标识，最多 1024 字节。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileItem-id: string--><!--Device-VirtualFileItem-id: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## size

```TypeScript
size: number
```

必填的文件字节数，必须为非负整数；0 表示真实空文件。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileItem-size: long--><!--Device-VirtualFileItem-size: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'file'
```

文件节点类型。

**类型：** 'file'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualFileItem-readonly type: 'file'--><!--Device-VirtualFileItem-readonly type: 'file'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
