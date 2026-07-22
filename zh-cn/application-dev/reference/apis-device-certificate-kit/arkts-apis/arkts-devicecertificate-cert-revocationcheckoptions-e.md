# RevocationCheckOptions

表示证书链在线校验证书吊销状态选项的枚举。

**起始版本：** 12

<!--Device-cert-enum RevocationCheckOptions--><!--Device-cert-enum RevocationCheckOptions-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_PREFER_OCSP

```TypeScript
REVOCATION_CHECK_OPTION_PREFER_OCSP = 0
```

优先采用OCSP进行校验，默认采用CRL校验。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_PREFER_OCSP = 0--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_PREFER_OCSP = 0-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_ACCESS_NETWORK

```TypeScript
REVOCATION_CHECK_OPTION_ACCESS_NETWORK = 1
```

支持通过访问网络获取CRL或OCSP响应进行吊销状态的校验，默认为关闭。仅支持通过证书中的CDP扩展中获取首个CRL分发点地址以检查证书吊销状态，或通过AIA扩展获取首个OCSP服务器地址以进行吊销状态验证，且仅支持http协议。必须声明ohos.permission.INTERNET权限。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_ACCESS_NETWORK = 1--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_ACCESS_NETWORK = 1-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER

```TypeScript
REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER = 2
```

当ACCESS_NETWORK选项打开时有效，如果优选的校验方法由于网络原因导致无法校验证书状态，则采用备选的方案进行校验。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER = 2--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER = 2-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_FALLBACK_LOCAL

```TypeScript
REVOCATION_CHECK_OPTION_FALLBACK_LOCAL = 3
```

当ACCESS_NETWORK选项打开时有效，如果在线获取CRL和OCSP响应都由于网络的原因导致无法校验证书状态，则采用本地设置的CRL和OCSP响应进行校验。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_FALLBACK_LOCAL = 3--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_FALLBACK_LOCAL = 3-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE

```TypeScript
REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE = 4
```

当ACCESS_NETWORK选项打开时有效。如果开启了该能力，对终端实体证书OCSP或CRL校验成功，则会继续校验中间证书的吊销情况。默认关闭。
> **说明：**  
>  
> 当前能力与REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT不能同时开启。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE = 4--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE = 4-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT

```TypeScript
REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT = 5
```

如果开启了该能力，则会拿本地吊销列表校验终端实体证书的吊销情况。默认关闭。
> **说明：**  
>  
> 当前能力与REVOCATION_CHECK_OPTION_CHECK_INTERMEDIATE_CA_ONLINE不能同时开启。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT = 5--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_LOCAL_CRL_ONLY_CHECK_END_ENTITY_CERT = 5-End-->

**系统能力：** SystemCapability.Security.Cert

## REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR

```TypeScript
REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR = 6
```

如果开启了该能力，通过访问网络获取CRL或OCSP响应进行吊销状态的校验时，忽略网络不可达错误。默认关闭，默认情况下，网络不可达可能导致证书链校验失败。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR = 6--><!--Device-RevocationCheckOptions-REVOCATION_CHECK_OPTION_IGNORE_NETWORK_ERROR = 6-End-->

**系统能力：** SystemCapability.Security.Cert

