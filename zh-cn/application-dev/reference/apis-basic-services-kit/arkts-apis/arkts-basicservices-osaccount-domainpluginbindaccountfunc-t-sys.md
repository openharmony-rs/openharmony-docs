# DomainPluginBindAccountFunc（系统接口）

```TypeScript
type DomainPluginBindAccountFunc = (domainAccountInfo: DomainAccountInfo,
    localId: int, callback: AsyncCallback<void>) => void
```

绑定指定的域账号。

**起始版本：** 23

<!--Device-osAccount-type DomainPluginBindAccountFunc = (domainAccountInfo: DomainAccountInfo,    localId: int, callback: AsyncCallback<void>) => void--><!--Device-osAccount-type DomainPluginBindAccountFunc = (domainAccountInfo: DomainAccountInfo,    localId: int, callback: AsyncCallback<void>) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 表示域账号信息。 |
| localId | int | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 表示绑定结果回调。 |

