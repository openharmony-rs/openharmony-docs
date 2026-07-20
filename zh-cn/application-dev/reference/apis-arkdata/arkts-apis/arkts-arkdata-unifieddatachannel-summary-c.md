# Summary

描述统一数据对象的数据摘要，包括数据类型和大小。

**起始版本：** 10

<!--Device-unifiedDataChannel-class Summary--><!--Device-unifiedDataChannel-class Summary-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## overview

```TypeScript
get overview(): Record<string, number>
```

统一数据对象中所有类型与该类型数据记录大小的映射关系，其中数据大小单位为Byte。当获取到的统一数据对象为空时，此overview属性值为空。

**类型：** Record&lt;string, number&gt;

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Summary-get overview(): Record<string, long>--><!--Device-Summary-get overview(): Record<string, long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## summary

```TypeScript
set summary(value: Record<string, number>)
```

是一个字典类型对象，key表示数据类型（见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)），value为统一数据对象中该类型记录大小总和（单位：Byte）。

**类型：** Record&lt;string, number&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Summary-set summary(value: Record<string, long>)--><!--Device-Summary-set summary(value: Record<string, long>)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## totalSize

```TypeScript
set totalSize(value: number)
```

统一数据对象内记录总大小（单位：Byte）。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Summary-set totalSize(value: long)--><!--Device-Summary-set totalSize(value: long)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

