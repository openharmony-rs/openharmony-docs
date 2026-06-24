# getResourceId

## getResourceId

```TypeScript
function getResourceId(providerName: string, params: HuksExternalCryptoParam[]): Promise<string>
```

获取密钥扩展能力的资源ID。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| providerName | string | 是 | 提供者名称，建议包含厂商信息，全局唯一，长度最大为128字节。 |
| params | HuksExternalCryptoParam[] | 是 | 获取资源ID所需的属性参数。必选TAG包括：<br/>[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md#HuksExternalCryptoTagType)、<br/>[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md#HuksExternalCryptoTagType)、<br/>[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md#HuksExternalCryptoTagType)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-API) | API is not supported. |
| [12000002](../../errorcode-universal.md#12000002-The) | The ability name, bundle name parameter or resource information is missing. |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed. |
| [12000011](../../errorcode-universal.md#12000011-The) | The provider is not found. |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameters are abnormal.<br/>This error may occur if the process function is not found, or due to other issues. |
| [12000014](../../errorcode-universal.md#12000014-The) | The memory is insufficient. |
| [12000018](../../errorcode-universal.md#12000018-Input) | Input parameters are invalid. Possible causes:<br/>1. The providerName length is invalid.<br/>2. The parameters contain invalid tags or invalid value types. |
| [12000020](../../errorcode-universal.md#12000020-The) | The provider operation failed.<br/>This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000024](../../errorcode-universal.md#12000024-The) | The provider or UKey is busy. |

**示例：**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const abilityName = "CryptoExtension";
const bundleName = "com.example.cryptoapplication";
// 资源信息，格式和内容由厂商自定义
const resourceInfo = "vendor_defined_resource_info";

const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array(abilityName)
  },
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
    value: StringToUint8Array(bundleName)
  },
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
    value: StringToUint8Array(resourceInfo)
  }
];

huksExternalCrypto.getResourceId(providerName, extProperties)
    .then((resourceId) => {
      console.info(`promise: getResourceId success, resourceId: ${resourceId}`);
    });

```

