# GetDomainAccessTokenOptions（系统接口）

表示获取域访问令牌的选项。

**起始版本：** 10

<!--Device-osAccount-interface GetDomainAccessTokenOptions--><!--Device-osAccount-interface GetDomainAccessTokenOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## businessParams

```TypeScript
businessParams: Record<string, Object>
```

业务参数，由业务方根据请求协议自定义。

**类型：** Record<string, Object>

**起始版本：** 10

<!--Device-GetDomainAccessTokenOptions-businessParams: Record<string, Object>--><!--Device-GetDomainAccessTokenOptions-businessParams: Record<string, Object>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## callerUid

```TypeScript
callerUid: number
```

调用方唯一标识符。

**类型：** number

**起始版本：** 10

<!--Device-GetDomainAccessTokenOptions-callerUid: int--><!--Device-GetDomainAccessTokenOptions-callerUid: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## domainAccountInfo

```TypeScript
domainAccountInfo: DomainAccountInfo
```

域账号的信息。

**类型：** DomainAccountInfo

**起始版本：** 10

<!--Device-GetDomainAccessTokenOptions-domainAccountInfo: DomainAccountInfo--><!--Device-GetDomainAccessTokenOptions-domainAccountInfo: DomainAccountInfo-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## domainAccountToken

```TypeScript
domainAccountToken: Uint8Array
```

域账号的令牌。

**类型：** Uint8Array

**起始版本：** 10

<!--Device-GetDomainAccessTokenOptions-domainAccountToken: Uint8Array--><!--Device-GetDomainAccessTokenOptions-domainAccountToken: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

