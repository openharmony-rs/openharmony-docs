# ExtensionValue（系统接口）

当前数据记录的扩展信息。

**起始版本：** 11

<!--Device-cloudExtension-export interface ExtensionValue--><!--Device-cloudExtension-export interface ExtensionValue-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createTime

```TypeScript
readonly createTime: number
```

创建行数据的时间（ms）。

**类型：** number

**起始版本：** 11

<!--Device-ExtensionValue-readonly createTime: long--><!--Device-ExtensionValue-readonly createTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## id

```TypeScript
readonly id: string
```

执行插入操作时系统自动生成的ID。

**类型：** string

**起始版本：** 11

<!--Device-ExtensionValue-readonly id: string--><!--Device-ExtensionValue-readonly id: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## modifyTime

```TypeScript
readonly modifyTime: number
```

修改行数据的时间（ms）。

**类型：** number

**起始版本：** 11

<!--Device-ExtensionValue-readonly modifyTime: long--><!--Device-ExtensionValue-readonly modifyTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## operation

```TypeScript
readonly operation: Flag
```

对行数据所做的操作。

**类型：** Flag

**起始版本：** 11

<!--Device-ExtensionValue-readonly operation: Flag--><!--Device-ExtensionValue-readonly operation: Flag-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

