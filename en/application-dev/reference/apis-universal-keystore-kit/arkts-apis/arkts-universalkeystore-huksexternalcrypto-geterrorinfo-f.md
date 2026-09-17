# getErrorInfo

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## getErrorInfo

```TypeScript
function getErrorInfo(): HuksExternalErrorInfo
```

Get the detailed error information.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Return value:**

| Type | Description |
| --- | --- |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | The returned error information. |

**Examples**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const resourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: "testKey"
});

const params: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
    value: StringToUint8Array(pin)
  }
];

try {
  await huksExternalCrypto.authUkeyPin(resourceId, params);
} catch (error) {
  const errorInfo = huksExternalCrypto.getErrorInfo();
  console.info(`errno: ${errorInfo.errno}`);
  console.info(`errorDesc: ${errorInfo.errorDesc}`);
}
```
