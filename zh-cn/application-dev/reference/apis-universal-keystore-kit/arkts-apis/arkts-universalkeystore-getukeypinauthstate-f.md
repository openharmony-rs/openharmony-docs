# getUkeyPinAuthState

## getUkeyPinAuthState

```TypeScript
function getUkeyPinAuthState(resourceId: string, params?: Array<HuksExternalCryptoParam>): Promise<HuksExternalPinAuthState>
```

获取PIN码认证状态。使用Promise异步回调。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID，可通过[导出证书的接口](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-openauthorizedialog-f.md#openauthorizedialog-2)获取，其结果中附带资源ID。 |
| params | Array&lt;HuksExternalCryptoParam&gt; | 否 | 操作的属性。非系统应用传入[HUKS_EXT_CRYPTO_TAG_UID](arkts-universalkeystore-huksexternalcryptotagtype-e.md)是非法参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksExternalPinAuthState&gt; | Promise对象，返回认证结果。<br>HUKS_EXT_CRYPTO_PIN_NO_AUTH 表示未认证；HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED 表示认证成功；HUKS_EXT_CRYPTO_PIN_LOCKED 表示PIN被锁定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | the UKey driver operation failed. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist. This may happenbecause the resource ID has not been opened. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter is abnormal.This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the input parameter is invalid. |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed. |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy. |

**示例：**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
    .then((data) => {
      console.info(`promise: getUkeyPinAuthState success, data: ${data}`);
    });

```

