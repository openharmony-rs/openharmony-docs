# ExtensionValue (System API)

```TypeScript
export interface ExtensionValue
```

Represents additional information about a data record.

**Since:** 11

<!--Device-cloudExtension-export interface ExtensionValue--><!--Device-cloudExtension-export interface ExtensionValue-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## createTime

```TypeScript
readonly createTime: number
```

Time when a row of data is created, in ms.

**Type:** number

**Since:** 11

<!--Device-ExtensionValue-readonly createTime: long--><!--Device-ExtensionValue-readonly createTime: long-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## id

```TypeScript
readonly id: string
```

ID generated when data is inserted. An ID is generated for each row when data is first inserted to the cloud. The ID must be unique for each table.

**Type:** string

**Since:** 11

<!--Device-ExtensionValue-readonly id: string--><!--Device-ExtensionValue-readonly id: string-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## modifyTime

```TypeScript
readonly modifyTime: number
```

Time when a row of data is modified, in ms.

**Type:** number

**Since:** 11

<!--Device-ExtensionValue-readonly modifyTime: long--><!--Device-ExtensionValue-readonly modifyTime: long-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## operation

```TypeScript
readonly operation: Flag
```

Operation performed.

**Type:** [Flag](arkts-arkdata-cloudextension-flag-e-sys.md)

**Since:** 11

<!--Device-ExtensionValue-readonly operation: Flag--><!--Device-ExtensionValue-readonly operation: Flag-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
