# DomainPluginIsAccountTokenValidFunc（系统接口）

```TypeScript
type DomainPluginIsAccountTokenValidFunc = (
    domainAccountInfo: DomainAccountInfo,
    token: Uint8Array,
    callback: AsyncCallback<boolean>
  ) => void
```

检查指定的域账号令牌是否有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-type DomainPluginIsAccountTokenValidFunc = (    domainAccountInfo: DomainAccountInfo,    token: Uint8Array,    callback: AsyncCallback<boolean>  ) => void--><!--Device-osAccount-type DomainPluginIsAccountTokenValidFunc = (    domainAccountInfo: DomainAccountInfo,    token: Uint8Array,    callback: AsyncCallback<boolean>  ) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 表示域账号信息。 |
| token | Uint8Array | 是 | 表示域账号令牌。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 表示检查结果回调。true表示指定的域账号令牌是有效的；false表示指定的域账号令牌是无效的。 |

