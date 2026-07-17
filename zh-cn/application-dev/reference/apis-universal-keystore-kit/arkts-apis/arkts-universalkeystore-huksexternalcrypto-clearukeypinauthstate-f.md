# clearUkeyPinAuthState

## 导入模块

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## clearUkeyPinAuthState

```TypeScript
function clearUkeyPinAuthState(resourceId: string): Promise<void>
```

清除指定资源ID的PIN码认证状态。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-huksExternalCrypto-function clearUkeyPinAuthState(resourceId: string): Promise<void>--><!--Device-huksExternalCrypto-function clearUkeyPinAuthState(resourceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | 资源ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | API is not supported. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | Failed to call the UKey driver interface.Please check the UKey connection and driver status. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The cached resource ID not found. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameters are abnormal.This may occur if the process function is null, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | The input parameters are invalid. Possible causes:1. The resourceId length is invalid. |
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

huksExternalCrypto.clearUkeyPinAuthState(testResourceId)
    .then(() => {
      console.info('promise: clearUkeyPinAuthState success.');
    });

```

