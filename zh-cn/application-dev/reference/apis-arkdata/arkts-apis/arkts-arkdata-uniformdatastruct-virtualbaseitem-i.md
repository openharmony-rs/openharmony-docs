# VirtualBaseItem

```TypeScript
interface VirtualBaseItem
```

描述按需提供拖拽数据的虚拟文件或目录的公共元数据。

**起始版本：** 26.1.0

<!--Device-uniformDataStruct-interface VirtualBaseItem--><!--Device-uniformDataStruct-interface VirtualBaseItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## modifyTime

```TypeScript
modifyTime: number
```

最近修改时间，单位为自 Unix 纪元开始的毫秒数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualBaseItem-modifyTime: long--><!--Device-VirtualBaseItem-modifyTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## name

```TypeScript
name: string
```

节点名称，最多 255 字节，不得为 . 或 ..，不得包含斜杠、反斜杠或空字符。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualBaseItem-name: string--><!--Device-VirtualBaseItem-name: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## type

```TypeScript
readonly type: 'file' | 'dir'
```

节点类型。

**类型：** 'file' &#124; 'dir'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualBaseItem-readonly type: 'file' | 'dir'--><!--Device-VirtualBaseItem-readonly type: 'file' | 'dir'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
