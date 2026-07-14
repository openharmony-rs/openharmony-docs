# ValidationPolicyType

表示证书链在线校验策略的枚举。

**起始版本：** 12

**系统能力：** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_X509

```TypeScript
VALIDATION_POLICY_TYPE_X509 = 0
```

默认值，不需要校验证书中的sslHostname或dNSName。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_SSL

```TypeScript
VALIDATION_POLICY_TYPE_SSL = 1
```

需要校验证书中的sslHostname字段。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Cert

