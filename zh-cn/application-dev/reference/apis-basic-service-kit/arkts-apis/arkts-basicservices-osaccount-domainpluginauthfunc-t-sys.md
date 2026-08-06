# DomainPluginAuthFunc（系统接口）

```TypeScript
type DomainPluginAuthFunc = (domainAccountInfo: DomainAccountInfo,
    credential: Uint8Array, callback: IUserAuthCallback) => void
```

认证指定的域账号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-osAccount-type DomainPluginAuthFunc = (domainAccountInfo: DomainAccountInfo,    credential: Uint8Array, callback: IUserAuthCallback) => void--><!--Device-osAccount-type DomainPluginAuthFunc = (domainAccountInfo: DomainAccountInfo,    credential: Uint8Array, callback: IUserAuthCallback) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示域账号信息。  |
| credential | Uint8Array | 是 | 表示域账号的凭据。  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示认证结果回调。  |

