# setProperty

## setProperty

```TypeScript
function setProperty(resourceId: string, propertyId: string, params?: HuksExternalCryptoParam[]): Promise<void>
```

The set-type operations of the external crypto extension support calling custom interfaces.
However, the custom interface must be registered with the provider.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID，可通过<br/>[导出证书的接口](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog-2)<br/>获取，该接口的返回结果中附带resourceId。 |
| propertyId | string | 是 | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，应用开发者需要针对接口名进行适配。 |
| params | HuksExternalCryptoParam[] | 否 | 需要传递给<br/>[Extension Ability](arkts-security-cryptoextensionability.md)的输入参数。非系统应用传入<br/>[HUKS_EXT_CRYPTO_TAG_UID](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md#HuksExternalCryptoTagType)是非法参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回调用接口的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-API) | API is not supported. |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed. |
| [12000006](../../errorcode-universal.md#12000006-Failed) | Failed to call the UKey driver interface.<br/>Please check the UKey connection and driver status. |
| [12000011](../../errorcode-universal.md#12000011-The) | The cached resource ID not found. |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameters are abnormal.<br/>This may occur if the process function is null, or due to other issues. |
| [12000014](../../errorcode-universal.md#12000014-The) | The memory is insufficient. |
| [12000018](../../errorcode-universal.md#12000018-The) | The input parameters are invalid. Possible causes:<br/>1. The resourceId or propertyId length is invalid.<br/>2. The parameters contain invalid tags or invalid value types. |
| [12000020](../../errorcode-universal.md#12000020-The) | The provider operation failed.<br/>This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000021](../../errorcode-universal.md#12000021-The) | The UKey PIN is locked. |
| [12000023](../../errorcode-universal.md#12000023-The) | The UKey PIN is not authenticated. |
| [12000024](../../errorcode-universal.md#12000024-The) | The provider or UKey is busy. |

**示例：**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

const propertyId = "SKF_SetDevInfo";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.setProperty(testResourceId, propertyId, extProperties)
      .then(() => {
        console.info('promise: setProperty success.');
      });
  } catch (error) {
    console.error(`promise: setProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}

```

