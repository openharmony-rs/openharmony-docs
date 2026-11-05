# VirtualDirItem

```TypeScript
interface VirtualDirItem extends VirtualBaseItem
```

描述虚拟目录及其可选子节点。目录不要求提供文件大小。

**继承/实现关系：** VirtualDirItem extends [VirtualBaseItem](arkts-arkdata-uniformdatastruct-virtualbaseitem-i.md)

**起始版本：** 26.1.0

<!--Device-uniformDataStruct-interface VirtualDirItem extends VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualDirItem extends VirtualBaseItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## subItems

```TypeScript
subItems?: Array<VirtualItemType>
```

落入方枚举目录时可访问的子节点。

**类型：** Array&lt;[VirtualItemType](arkts-arkdata-uniformdatastruct-virtualitemtype-t.md)&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualDirItem-subItems?: Array<VirtualItemType>--><!--Device-VirtualDirItem-subItems?: Array<VirtualItemType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'dir'
```

目录节点类型。

**类型：** 'dir'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualDirItem-readonly type: 'dir'--><!--Device-VirtualDirItem-readonly type: 'dir'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
