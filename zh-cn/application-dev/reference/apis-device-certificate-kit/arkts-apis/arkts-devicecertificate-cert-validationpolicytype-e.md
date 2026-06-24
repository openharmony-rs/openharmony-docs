# ValidationPolicyType

```TypeScript
enum ValidationPolicyType
```

表示证书链在线校验策略的枚举。

**起始版本：** 12

**系统能力：** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_X509

```TypeScript
VALIDATION_POLICY_TYPE_X509 = 0
```

默认值，不需要校验证书中的sslHostname或dNSName。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

## VALIDATION_POLICY_TYPE_SSL

```TypeScript
VALIDATION_POLICY_TYPE_SSL = 1
```

需要校验证书中的sslHostname字段。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

