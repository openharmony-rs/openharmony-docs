# Statistic

描述数据库表的端云同步过程的统计信息。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## failed

```TypeScript
failed: number
```

表示数据库表中端云同步失败的行数。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## remained

```TypeScript
remained: number
```

表示数据库表中端云同步剩余未执行的行数。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## successful

```TypeScript
successful: number
```

表示数据库表中端云同步成功的行数。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## total

```TypeScript
total: number
```

表示数据库表中需要端云同步的总行数。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
