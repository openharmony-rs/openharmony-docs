# getErrorInfo

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## getErrorInfo

```TypeScript
function getErrorInfo(): HuksExternalErrorInfo
```

查询上次接口调用产生的详细错误信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-huksExternalCrypto-function getErrorInfo(): HuksExternalErrorInfo--><!--Device-huksExternalCrypto-function getErrorInfo(): HuksExternalErrorInfo-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | 返回的详细错误信息。 |

**示例：**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const resourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: "testKey"
});
const pin = "123456"; // 此处为示例，实际业务中应替换为真实的用户PIN码
const params: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
    value: stringToUint8Array(pin)
  }
];

async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.authUkeyPin(resourceId, params);
  } catch (error) {
    const errorInfo = huksExternalCrypto.getErrorInfo();
    console.info(`errno: ${errorInfo.errno}`);
    console.info(`errorDesc: ${errorInfo.errorDesc}`);
  }
}

```

