# anonAttestKeyItem

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="anonattestkeyitem"></a>
## anonAttestKeyItem

```TypeScript
function anonAttestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void
```

获取匿名化密钥证书。使用callback异步回调。

该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。

> **说明：**  
>  
> 获取[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥证书需要ohos.permission.ACCESS_SE_KEY权限。

<!--RP1--><!--RP1End-->

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function anonAttestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void--><!--Device-huks-function anonAttestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksReturnResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，存放待获取证书密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于获取证书时指定所需参数与数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksReturnResult&gt; | 是 | 回调函数。当获取匿名化密钥证书成功时，err为undefined，data为获取到的HuksReturnResult；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
/* 以获取RSA匿名化密钥证书为例 */
import { huks } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

let securityLevel = stringToUint8Array('sec_level');
let challenge = stringToUint8Array('challenge_data');
let versionInfo = stringToUint8Array('version_info');
let keyAliasString = "key anon attest";

async function generateKeyThenAttestKey(): Promise<void> {
  let aliasString = keyAliasString;
  let aliasUint8 = stringToUint8Array(aliasString);
  /* 1. 配置密钥生成参数 */
  let generateProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_RSA
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_PSS
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_GENERATE_TYPE,
      value: huks.HuksKeyGenerateType.HUKS_KEY_GENERATE_TYPE_DEFAULT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_ECB
    }
  ];
  let generateOptions: huks.HuksOptions = {
    properties: generateProperties
  };
  /* 2. 配置匿名证明参数 */
  let anonAttestProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO,
      value: securityLevel
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
      value: challenge
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_VERSION_INFO,
      value: versionInfo
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
      value: aliasUint8
    }
  ];
  let anonAttestOptions: huks.HuksOptions = {
    properties: anonAttestProperties
  };
  /* 3. 生成密钥并获取匿名密钥证明 */
  huks.generateKeyItem(aliasString, generateOptions, (error) => {
    if (error) {
      console.error(`callback: generateKeyItem failed`);
    } else {
      console.info(`callback: generateKeyItem success`);
      huks.anonAttestKeyItem(aliasString, anonAttestOptions, (error) => {
        if (error) {
          console.error(`callback: anonAttestKeyItem failed`);
        } else {
          console.info(`callback: anonAttestKeyItem success`);
        }
      });
    }
  });
}

```


<a id="anonattestkeyitem-1"></a>
## anonAttestKeyItem

```TypeScript
function anonAttestKeyItem(keyAlias: string, options: HuksOptions): Promise<HuksReturnResult>
```

获取匿名化密钥证书。使用Promise异步回调。

该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。

> **说明：**  
>  
> 获取[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥证书需要ohos.permission.ACCESS_SE_KEY权限。

<!--RP1--><!--RP1End-->

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function anonAttestKeyItem(keyAlias: string, options: HuksOptions): Promise<HuksReturnResult>--><!--Device-huks-function anonAttestKeyItem(keyAlias: string, options: HuksOptions): Promise<HuksReturnResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，存放待获取证书密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于获取证书时指定所需参数与数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise对象，返回调用接口的结果。当调用成功时，HuksReturnResult的certChains成员为获取到的证书链。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing<br>**适用版本：** 11+ |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid<br>**适用版本：** 11+ |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
/* 以获取RSA匿名化密钥证书为例 */
import { huks } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

let securityLevel = stringToUint8Array('sec_level');
let challenge = stringToUint8Array('challenge_data');
let versionInfo = stringToUint8Array('version_info');
let keyAliasString = "key anon attest";

/* 1. 生成密钥 */
async function generateKey(alias: string): Promise<void> {
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_RSA
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_PSS
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_GENERATE_TYPE,
      value: huks.HuksKeyGenerateType.HUKS_KEY_GENERATE_TYPE_DEFAULT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_ECB
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await huks.generateKeyItem(alias, options);
}

/* 2. 获取匿名化密钥证书 */
async function anonAttestKey(): Promise<void> {
  let aliasString = keyAliasString;
  let aliasUint8 = stringToUint8Array(aliasString);

  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO,
      value: securityLevel
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
      value: challenge
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_VERSION_INFO,
      value: versionInfo
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
      value: aliasUint8
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await generateKey(aliasString);
  await huks.anonAttestKeyItem(aliasString, options);
}

```

