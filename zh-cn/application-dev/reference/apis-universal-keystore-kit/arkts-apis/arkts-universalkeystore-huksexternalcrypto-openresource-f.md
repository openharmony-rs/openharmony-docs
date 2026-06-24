# openResource

## openResource

```TypeScript
function openResource(resourceId: string, params?: HuksExternalCryptoParam[]): Promise<void>
```

打开指定资源ID的资源。使用Promise异步回调。

> **说明：**
>
> 打开的资源必须使用[closeResource](arkts-universalkeystore-huksexternalcrypto-closeresource-f.md#closeResource-1)关闭。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID。可通过<br/>[证书选择接口](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog-2)<br/>获取keyUri作为resourceId，或通过[getResourceId](arkts-universalkeystore-huksexternalcrypto-getresourceid-f.md#getResourceId-1)获取外部密钥管理扩展的资源ID。 |
| params | HuksExternalCryptoParam[] | 否 | 需要传递给<br/>[Extension Ability](arkts-security-cryptoextensionability.md)的输入参数。不传入时，不向Extension Ability传递额外参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-API) | API is not supported. |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed. |
| [12000006](../../errorcode-universal.md#12000006-Failed) | Failed to call the UKey driver interface.<br/>Please check the UKey connection and driver status. |
| [12000011](../../errorcode-universal.md#12000011-The) | The cached resource ID is not found.<br/>This may happen because the resource ID has not been opened. |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameters are abnormal.<br/>This error may occur if the process function is not found, or due to other issues. |
| [12000014](../../errorcode-universal.md#12000014-The) | The memory is insufficient. |
| [12000017](../../errorcode-universal.md#12000017-The) | The resource with the resource ID is already open. |
| [12000018](../../errorcode-universal.md#12000018-Input) | Input parameters are invalid. Possible causes:<br/>1. The resourceId length is invalid.<br/>2. The parameters contain invalid tags or invalid value types. |
| [12000020](../../errorcode-universal.md#12000020-The) | The provider operation failed.<br/>This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000024](../../errorcode-universal.md#12000024-The) | The provider or UKey is busy. |
| [12000025](../../errorcode-universal.md#12000025-The) | The opened resources exceed the limit. |

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

huksExternalCrypto.openResource(testResourceId)
    .then(() => {
      console.info('promise: openResource success.');
    });

```

