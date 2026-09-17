# DistributedConfig

记录表的分布式配置信息。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## references

```TypeScript
references?: Array<Reference>
```

设置表之间的关联关系，可以设置多个字段的关联，子表和父表关联字段的值必须相同。默认数据库表之间无关联关系。

**系统接口：** 此接口为系统接口。

从API version 11开始，支持此可选参数。

**类型：** Array&lt;[Reference](arkts-arkdata-relationalstore-reference-i-sys.md)&gt;

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。
