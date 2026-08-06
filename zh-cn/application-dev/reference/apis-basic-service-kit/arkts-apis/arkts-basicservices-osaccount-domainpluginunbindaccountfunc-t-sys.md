# DomainPluginUnbindAccountFunc（系统接口）

```TypeScript
type DomainPluginUnbindAccountFunc = (domainAccountInfo: DomainAccountInfo,
    callback: AsyncCallback<void>) => void
```

解绑指定的域账号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-osAccount-type DomainPluginUnbindAccountFunc = (domainAccountInfo: DomainAccountInfo,    callback: AsyncCallback<void>) => void--><!--Device-osAccount-type DomainPluginUnbindAccountFunc = (domainAccountInfo: DomainAccountInfo,    callback: AsyncCallback<void>) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示域账号信息。  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 表示绑定结果回调。  |

