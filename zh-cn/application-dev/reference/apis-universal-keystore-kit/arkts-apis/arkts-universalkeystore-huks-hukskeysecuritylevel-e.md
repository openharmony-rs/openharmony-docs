# HuksKeySecurityLevel

表示密钥安全级别的枚举。

**起始版本：** 26.0.0

<!--Device-huks-export enum HuksKeySecurityLevel--><!--Device-huks-export enum HuksKeySecurityLevel-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_KEY_SECURITY_LEVEL_TEE

```TypeScript
HUKS_KEY_SECURITY_LEVEL_TEE = 0
```

密钥在可信执行环境中生成并使用。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeySecurityLevel-HUKS_KEY_SECURITY_LEVEL_TEE = 0--><!--Device-HuksKeySecurityLevel-HUKS_KEY_SECURITY_LEVEL_TEE = 0-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_KEY_SECURITY_LEVEL_SE

```TypeScript
HUKS_KEY_SECURITY_LEVEL_SE = 1
```

密钥在安全环境中生成并使用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_SE_KEY

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeySecurityLevel-HUKS_KEY_SECURITY_LEVEL_SE = 1--><!--Device-HuksKeySecurityLevel-HUKS_KEY_SECURITY_LEVEL_SE = 1-End-->

**系统能力：** SystemCapability.Security.Huks.Core

