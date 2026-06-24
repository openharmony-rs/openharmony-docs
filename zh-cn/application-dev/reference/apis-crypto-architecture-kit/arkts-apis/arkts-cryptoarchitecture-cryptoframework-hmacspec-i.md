# HmacSpec

消息认证码参数[MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md#MacSpec)的子类，作为HMAC消息验证码计算的输入。

> **说明：**
>
> mdName是必选参数，表示HMAC摘要算法。

**继承/实现关系：** HmacSpec extends [MacSpec](arkts-cryptoarchitecture-cryptoframework-macspec-i.md#MacSpec)

**起始版本：** 18

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

## mdName

```TypeScript
mdName: string
```

摘要算法名。

**类型：** string

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

