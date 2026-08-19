# DomainPluginAuthWithTokenFunc（系统接口）

```TypeScript
type DomainPluginAuthWithTokenFunc = (domainAccountInfo: DomainAccountInfo,
    token: Uint8Array, callback: IUserAuthCallback) => void
```

使用授权令牌认证指定的域账号。

**起始版本：** 23

<!--Device-osAccount-type DomainPluginAuthWithTokenFunc = (domainAccountInfo: DomainAccountInfo,    token: Uint8Array, callback: IUserAuthCallback) => void--><!--Device-osAccount-type DomainPluginAuthWithTokenFunc = (domainAccountInfo: DomainAccountInfo,    token: Uint8Array, callback: IUserAuthCallback) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 表示域账号信息。 |
| token | Uint8Array | 是 | 表示PIN码或生物识别认证成功时生成的授权令牌。 |
| callback | IUserAuthCallback | 是 | 表示认证结果回调。 |

