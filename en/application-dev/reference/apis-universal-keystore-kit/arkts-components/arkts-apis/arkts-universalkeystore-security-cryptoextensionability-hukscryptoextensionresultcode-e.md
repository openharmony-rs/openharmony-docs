# HuksCryptoExtensionResultCode

Enum for crypto extension ability result code, used by HuksCryptoExtensionResult.resultCode.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL = 34800000
```

An error occurred in the crypto extension. Possible causes:

1. The input parameter is invalid.
2. The crypto extension encountered an unresolvable error state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST = 34800001
```

The UKey does not exist. Possible causes:

1. The UKey has been removed.
2. The crypto extension maintained an error UKey state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL = 34800002
```

The UKey driver error. This means an unknown error has occurred in the UKey driver.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH = 34800003
```

The UKey PIN is not authenticated. Please verify the UKey PIN first.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST = 34800004
```

The handle does not exist. Possible causes:

1. The handle you entered is invalid.
2. The states of huks service and crypto extension are inconsistent. Due to an exception,
the handle held by huks service was not released.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE = 34800005
```

The handle is unavailable, possibly due to an inconsistent state between the crypto extension and the UKey.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT = 34800006
```

The UKey PIN is not correct. Please check the PIN you entered.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

## HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED

```TypeScript
HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED = 34800007
```

The UKey PIN is locked because the maximum allowed number of attempts has been exceeded.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension
