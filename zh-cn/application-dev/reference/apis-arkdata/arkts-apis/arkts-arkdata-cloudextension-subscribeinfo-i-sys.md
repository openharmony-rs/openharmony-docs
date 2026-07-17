# SubscribeInfo（系统接口）

订阅信息

**起始版本：** 11

<!--Device-cloudExtension-export interface SubscribeInfo--><!--Device-cloudExtension-export interface SubscribeInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## expirationTime

```TypeScript
expirationTime: number
```

订阅过期时间（ms）。

**类型：** number

**起始版本：** 11

<!--Device-SubscribeInfo-expirationTime: long--><!--Device-SubscribeInfo-expirationTime: long-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## subscribe

```TypeScript
subscribe: Record<string, Array<SubscribeId>>
```

订阅信息。

**类型：** Record<string, Array<SubscribeId>>

**起始版本：** 11

<!--Device-SubscribeInfo-subscribe: Record<string, Array<SubscribeId>>--><!--Device-SubscribeInfo-subscribe: Record<string, Array<SubscribeId>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

