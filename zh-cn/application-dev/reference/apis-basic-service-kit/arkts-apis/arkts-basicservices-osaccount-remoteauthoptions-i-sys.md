# RemoteAuthOptions（系统接口）

表示远程认证的可选参数集合。

**起始版本：** 12

<!--Device-osAccount-interface RemoteAuthOptions--><!--Device-osAccount-interface RemoteAuthOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## collectorNetworkId

```TypeScript
collectorNetworkId?: string
```

凭据收集者的网络标识，默认为空。

**类型：** string

**起始版本：** 12

<!--Device-RemoteAuthOptions-collectorNetworkId?: string--><!--Device-RemoteAuthOptions-collectorNetworkId?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## collectorTokenId

```TypeScript
collectorTokenId?: number
```

凭据收集者的令牌标识，默认为undefined。

**类型：** number

**起始版本：** 12

<!--Device-RemoteAuthOptions-collectorTokenId?: int--><!--Device-RemoteAuthOptions-collectorTokenId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## verifierNetworkId

```TypeScript
verifierNetworkId?: string
```

凭据验证者的网络标识，默认为空。

**类型：** string

**起始版本：** 12

<!--Device-RemoteAuthOptions-verifierNetworkId?: string--><!--Device-RemoteAuthOptions-verifierNetworkId?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

