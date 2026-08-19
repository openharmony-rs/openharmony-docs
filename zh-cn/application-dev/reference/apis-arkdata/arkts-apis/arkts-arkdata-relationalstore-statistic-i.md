# Statistic

描述数据库表的端云同步过程的统计信息。

**起始版本：** 23

<!--Device-relationalStore-interface Statistic--><!--Device-relationalStore-interface Statistic-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## failed

```TypeScript
failed: int
```

表示数据库表中端云同步失败的行数。

**类型：** int

**起始版本：** 23

<!--Device-Statistic-failed: int--><!--Device-Statistic-failed: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## remained

```TypeScript
remained: int
```

表示数据库表中端云同步剩余未执行的行数。

**类型：** int

**起始版本：** 23

<!--Device-Statistic-remained: int--><!--Device-Statistic-remained: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## successful

```TypeScript
successful: int
```

表示数据库表中端云同步成功的行数。

**类型：** int

**起始版本：** 23

<!--Device-Statistic-successful: int--><!--Device-Statistic-successful: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## total

```TypeScript
total: int
```

表示数据库表中需要端云同步的总行数。

**类型：** int

**起始版本：** 23

<!--Device-Statistic-total: int--><!--Device-Statistic-total: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

