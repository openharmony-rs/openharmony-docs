# DomainPluginGetAccessTokenFunc（系统接口）

```TypeScript
type DomainPluginGetAccessTokenFunc = (options: GetDomainAccessTokenOptions,
    callback: AsyncCallback<Uint8Array>) => void
```

根据指定的选项获取域访问令牌。

**起始版本：** 23

<!--Device-osAccount-type DomainPluginGetAccessTokenFunc = (options: GetDomainAccessTokenOptions,    callback: AsyncCallback<Uint8Array>) => void--><!--Device-osAccount-type DomainPluginGetAccessTokenFunc = (options: GetDomainAccessTokenOptions,    callback: AsyncCallback<Uint8Array>) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetDomainAccessTokenOptions](arkts-basicservices-osaccount-getdomainaccesstokenoptions-i-sys.md) | 是 | 表示获取域访问令牌的选项。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Uint8Array&gt; | 是 | 表示结果回调。 |

