# LockInfo（系统接口）

云数据库锁信息。

**起始版本：** 11

<!--Device-cloudExtension-export interface LockInfo--><!--Device-cloudExtension-export interface LockInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## interval

```TypeScript
interval: number
```

云数据库锁的持续时间，单位为s。

**类型：** number

**起始版本：** 11

<!--Device-LockInfo-interval: int--><!--Device-LockInfo-interval: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## lockId

```TypeScript
lockId: number
```

锁ID。

**类型：** number

**起始版本：** 11

<!--Device-LockInfo-lockId: int--><!--Device-LockInfo-lockId: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

