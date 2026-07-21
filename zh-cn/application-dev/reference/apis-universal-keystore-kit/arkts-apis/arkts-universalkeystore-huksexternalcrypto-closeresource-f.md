# closeResource

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

<a id="closeresource"></a>
## closeResource

```TypeScript
function closeResource(resourceId: string, params?: HuksExternalCryptoParam[]): Promise<void>
```

关闭指定资源ID的资源。使用Promise异步回调。

该接口会回调[onClearUkeyPinAuthState]清理该资源关联的PIN认证状态，以及会回调[onFinishSession]清理该资源关联的会话handle。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-huksExternalCrypto-function closeResource(resourceId: string, params?: HuksExternalCryptoParam[]): Promise<void>--><!--Device-huksExternalCrypto-function closeResource(resourceId: string, params?: HuksExternalCryptoParam[]): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID。可通过[证书选择接口](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openauthorizedialog-1)获取keyUri作为resourceId，或通过[getResourceId](arkts-universalkeystore-huksexternalcrypto-getresourceid-f.md#getresourceid-1)获取外部密钥管理扩展的资源ID。 |
| params | [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)[] | 否 | 需要传递给[Extension Ability](arkts-security-cryptoextensionability.md)的输入参数。不传入时，不向Extension Ability传递额外参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | API is not supported. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | Failed to call the UKey driver interface.Please check the UKey connection and driver status. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameters are abnormal.This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | Input parameters are invalid. Possible causes:1. The resourceId length is invalid.2. The parameters contain invalid tags or invalid value types. |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | The provider operation failed.This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | The provider or UKey is busy. |

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

huksExternalCrypto.closeResource(testResourceId)
    .then(() => {
      console.info('promise: closeResource success.');
    });

```

