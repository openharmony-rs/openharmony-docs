# HuksSecureSignType

表示生成或导入密钥时，指定该密钥的签名类型。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_SECURE_SIGN_WITH_AUTHINFO

```TypeScript
HUKS_SECURE_SIGN_WITH_AUTHINFO = 1
```

表示签名类型为携带认证信息。生成或导入密钥时指定该字段，则在使用密钥进行签名时，对待签名的数据添加认证信息后进行签名。

**注意：**

携带的认证信息包含身份信息，开发者需在其隐私声明中对此身份信息的使用目的、存留策略和销毁方式进行说明。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

