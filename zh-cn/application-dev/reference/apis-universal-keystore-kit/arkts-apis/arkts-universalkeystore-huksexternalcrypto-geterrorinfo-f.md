# getErrorInfo

## getErrorInfo

```TypeScript
function getErrorInfo(): HuksExternalErrorInfo
```

查询上次接口调用产生的详细错误信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HuksExternalErrorInfo | 返回的详细错误信息。 |

**示例：**

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

