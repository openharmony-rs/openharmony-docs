# DomainPluginGetAccountInfoFunc（系统接口）

```TypeScript
type DomainPluginGetAccountInfoFunc = (options: GetDomainAccountInfoPluginOptions,
    callback: AsyncCallback<DomainAccountInfo>) => void
```

查询指定域账号的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-osAccount-type DomainPluginGetAccountInfoFunc = (options: GetDomainAccountInfoPluginOptions,    callback: AsyncCallback<DomainAccountInfo>) => void--><!--Device-osAccount-type DomainPluginGetAccountInfoFunc = (options: GetDomainAccountInfoPluginOptions,    callback: AsyncCallback<DomainAccountInfo>) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示域账号信息。  |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DomainAccountInfo&gt; | 是 | 表示查询结果回调。  |

