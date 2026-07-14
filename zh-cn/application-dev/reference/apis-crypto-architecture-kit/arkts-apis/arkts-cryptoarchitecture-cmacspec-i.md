# CmacSpec

消息认证码参数[MacSpec](arkts-cryptoarchitecture-macspec-i.md)的子类，作为CMAC计算的输入。

> **说明：**
>
> cipherName是必选参数，表示CMAC使用的对称密码算法。

**继承/实现关系：** CmacSpec extends [MacSpec](arkts-cryptoarchitecture-macspec-i.md)

**起始版本：** 18

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

## cipherName

```TypeScript
cipherName: string
```

CMAC使用的对称密码算法名。

**类型：** string

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

