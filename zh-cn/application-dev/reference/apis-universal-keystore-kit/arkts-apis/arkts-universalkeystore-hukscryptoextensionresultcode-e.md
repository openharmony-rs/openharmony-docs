# HuksCryptoExtensionResultCode

[HuksCryptoExtensionResult](arkts-universalkeystore-hukscryptoextensionresultcode-e.md)中的resultCode枚举值。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL = 34800000
```

密钥扩展错误。可能的原因：

1. 输入参数无效。
2. 密钥扩展出现无法解决的错误状态。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST = 34800001
```

UKey不存在。可能的原因：

1. UKey已被移除。
2. 密钥扩展陷入错误的UKey状态。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL = 34800002
```

UKey驱动出现未知错误。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH = 34800003
```

UKey PIN码未认证，需要先认证Ukey PIN码。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST = 34800004
```

句柄不存在。可能的原因：

1. 句柄无效。
2. HUKS服务和密钥扩展的状态不一致。由于异常情况，HUKS服务持有的句柄未能释放。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE = 34800005
```

句柄不可用。可能的原因：

密钥扩展和Ukey的状态不一致。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT = 34800006
```

UKey PIN码错误，需要检查输入的PIN码。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED = 34800007
```

UKey PIN码被锁。可能的原因：

PIN码输入错误次数过多。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

