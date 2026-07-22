# unregisterProvider

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## unregisterProvider

```TypeScript
function unregisterProvider(providerName: string, params?: Array<HuksExternalCryptoParam>): Promise<void>
```

注销指定的外部provider。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.CRYPTO_EXTENSION_REGISTER

<!--Device-huksExternalCrypto-function unregisterProvider(providerName: string, params?: Array<HuksExternalCryptoParam>): Promise<void>--><!--Device-huksExternalCrypto-function unregisterProvider(providerName: string, params?: Array<HuksExternalCryptoParam>): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| providerName | string | 是 | provider名称，最大长度为128。建议包含厂商信息，全局唯一，不要包含个人联系方式等敏感数据。如果provider注册了多个扩展能力，则该provider下的扩展能力都会被注销。 |
| params | Array&lt;HuksExternalCryptoParam&gt; | 否 | 操作时需传入的参数。<br>可以在param参数中指定[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md)，将根据“包名 + providerName +abilityName”注销对应的cryptoExtensionAbility。<br>如果未在params参数中指定[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md)，或者未传入params参数，则注销对应的providerName下的所有Provider。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | check permission failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | the provider is not found. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter is abnormal.This may happen for several reasons, such as the model already being unloaded. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid. |

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

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: stringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.unregisterProvider(providerName, extProperties)
    .then(() => {
        console.info('promise: unregisterProvider success.');
    });

```

