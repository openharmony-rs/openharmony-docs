# getProperty

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

<a id="getproperty"></a>
## getProperty

```TypeScript
function getProperty(resourceId: string, propertyId: string, params?: Array<HuksExternalCryptoParam>): Promise<Array<HuksExternalCryptoParam>>
```

调用此接口获取属性值并返回结果。使用Promise异步回调。

propertyId表示查询属性的ID信息，当前仅支持GMT 0016-2023中定义的SKF接口名作为属性ID，支持的ID包括如下：

- SKF_EnumDev  
- SKF_GetDevInfo  
- SKF_EnumApplication  
- SKF_EnumContainer

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-huksExternalCrypto-function getProperty(resourceId: string, propertyId: string, params?: Array<HuksExternalCryptoParam>): Promise<Array<HuksExternalCryptoParam>>--><!--Device-huksExternalCrypto-function getProperty(resourceId: string, propertyId: string, params?: Array<HuksExternalCryptoParam>): Promise<Array<HuksExternalCryptoParam>>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID，可通过[导出证书的接口](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openauthorizedialog-1)获取，该接口的返回结果中附带resourceId。 |
| propertyId | string | 是 | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，应用开发者需要针对接口名进行适配。 |
| params | Array&lt;HuksExternalCryptoParam&gt; | 否 | 需要传递给[Extension Ability](arkts-security-cryptoextensionability.md)的输入参数。非系统应用传入[HUKS_EXT_CRYPTO_TAG_UID](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md)是非法参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;HuksExternalCryptoParam&gt;&gt; | Promise对象，返回调用接口的结果。当调用成功时，返回结果为HuksExternalCryptoParam类型的数组，包含要查询的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | API is not supported. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | If the UKey driver operation failed. Possible causes:1. Error reported when the provider accesses the SKF interface of UKey. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | If the cached resource ID is not found. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter is abnormal.This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | If the memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | Input parameter is invalid. Possible causes:1. The resourceId or propertyId length is invalid.2. The params contains invalid tags or invalid value types. |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | If the provider operation failed. Possible causes:1. The provider experienced an internal processing error. |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | The UKey PIN is locked. |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | The UKey PIN is not authenticated. |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | If the provider or UKey is busy. |

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

let propertyId = "SKF_EnumDev";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

console.info('promise: await huksExternalCrypto getProperty.');
async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ` + JSON.stringify(data));
      });
  } catch (error) {
    console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}

```

