# anonAttestKeyItemOfflineAsUser（系统接口）

## anonAttestKeyItemOfflineAsUser

```TypeScript
function anonAttestKeyItemOfflineAsUser(userId: number, keyAlias: string,
      params: HuksParam[]): Promise<HuksReturnResult>
```

离线获取匿名证明证书。该接口使用promise返回结果。此操作不需要每次都需要网络连接，
比anonAttestKeyItemAsUser函数性能高。

> **说明**
> >
> -离线密钥证明依赖于网络。您需要定期连接网络才能使用此API更新离线证书。
> >
> -离线匿名密钥证明要求本地时间准确。否则，可能导致对端无法正常工作。验证证书过期。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID<br>取值范围为全体整数。 |
| keyAlias | string | 是 | 密钥的别名。 |
| params | HuksParam[] | 是 | 表示密钥证明操作的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise用于返回结果。如果操作成功。HuksReturnResult中的certChains包含获取到的证书链。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The app does not have sufficient permissions. Possible causes: Thecross-account permission is not granted, the system is not unlocked by the user, or the user does notexist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system apps use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The API is not supported. |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | The function is not supported. Possible causes:1. The algorithm mode is not supported.2. The group key is not supported.3. The extended encryption key is not supported. |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | The algorithm parameter is missing. |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | The algorithm parameter is invalid. |
| [12000004](../errorcode-huks.md#12000004-文件错误) | The file operation failed. |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | The IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | The encryption engine is faulty. |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The queried entity does not exist. |
| [12000012](../errorcode-huks.md#12000012-外部错误) | The device environment or input parameter is abnormal. |
| [12000014](../errorcode-huks.md#12000014-内存不足) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | The parameter is incorrect. Possible causes:1. A mandatory parameter is left empty.2. The parameter type is incorrect.3. The parameter verification failed. |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | The operation times out. This may be caused by network jitter.You can try again later. |
| 12000027 | The network is unavailable. Check network connections. |

**示例：**

以下代码示例接口调用的前置条件同上文[generateKeyItemAsUser](#huksgeneratekeyitemasuser)的前置条件

```TypeScript
/* 以ECC离线匿名密钥证明为例 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;
const keyAliasString = "key anon local attest as user";

const challenge = stringToUint8Array('challenge_data');

/* 1. 生成密钥 */
async function generateKey(alias: string) {
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_ECC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await huks.generateKeyItemAsUser(userId, alias, options);
}

/* 2. 离线获取匿名化密钥证书 */
async function anonAttestKeyItemOfflineAsUser() {
  let aliasString = keyAliasString;
  let aliasUint8 = stringToUint8Array(aliasString);
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
      value: challenge
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
      value: aliasUint8
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ];

  await generateKey(aliasString);
  await huks.anonAttestKeyItemOfflineAsUser(userId, aliasString, properties).then((data) => {
    console.info('anonAttestationOffline ok!')
    console.debug(`'CERT:${JSON.stringify(data)}`)
    for (let i = 0; data?.certChains?.length && i < data?.certChains?.length; ++i) {
      console.info(`CERT${i}是${data.certChains[i]}`)
    }
    console.info("anonAttestationOffline Success")
  }).catch((err: BusinessError) => {
    console.error("anonAttestationOffline fail，erroCode： " + err.code + " erroInfo： " + err.message)
  })
}

```

