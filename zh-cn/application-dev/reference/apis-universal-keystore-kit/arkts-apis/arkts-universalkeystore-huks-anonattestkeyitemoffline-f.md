# anonAttestKeyItemOffline

## anonAttestKeyItemOffline

```TypeScript
function anonAttestKeyItemOffline(keyAlias: string, params: HuksParam[]): Promise<HuksReturnResult>
```

����ģʽ�»�ȡ��������Կ֤�顣ʹ��Promise�첽�ص���

> **˵����**
>
> - ������Կ֤���������磬��Ҫ��������ʹ�øýӿ��Ը�������֤�飬�Ƽ�����ʹ������������Կ֤����
>
> - ����������Կ֤���豣֤����ʱ����׼ȷ�ģ�������ܵ��¶Զ�У��֤�鳬��ʧ�ܡ�

> **˵��**
> >
> - Offline key attestation depends on the network. You need to periodically connect to the network to use this API
> to update the offline certificate. Offline anonymous key attestation is recommended.
> >
> - Offline anonymous key attestation requires that the local time be accurate. Otherwise, the peer end may fail to
> verify the certificate expiration��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Ŵ���ȡ֤����Կ�ı����� |
| params | HuksParam[] | 是 | ���ڻ�ȡ֤��ʱָ��������������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise���󣬷��ص��ýӿڵĽ���������óɹ�ʱ��HuksReturnResult��certChains��ԱΪ��ȡ����֤������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-The) | The API is not supported. |
| [12000001](../../errorcode-universal.md#12000001-The) | The algorithm mode is not supported. |
| [12000004](../../errorcode-universal.md#12000004-The) | The file operation failed. |
| [12000005](../../errorcode-universal.md#12000005-The) | The IPC communication failed. |
| [12000006](../../errorcode-universal.md#12000006-The) | The encryption engine is faulty. |
| [12000011](../../errorcode-universal.md#12000011-The) | The queried entity does not exist. |
| [12000012](../../errorcode-universal.md#12000012-The) | The device environment or input parameter is abnormal. |
| [12000014](../../errorcode-universal.md#12000014-The) | The memory is insufficient. |
| [12000018](../../errorcode-universal.md#12000018-The) | The parameter is incorrect. Possible causes:<br/>1. A mandatory parameter is left empty.<br/>2. The parameter type is incorrect.<br/>3. The parameter verification failed.<br/>4. The group ID specified by the access group tag is invalid. |
| [12000024](../../errorcode-universal.md#12000024-The) | The operation times out. This may be caused by network jitter.<br/>You can try again later. |
| [12000027](../../errorcode-universal.md#12000027-The) | The network is unavailable. Check network connections. |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

let challenge = stringToUint8Array('challenge_data');
let keyAliasString = "key anon local attest";

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
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await huks.generateKeyItem(alias, options);
}

async function anonAttestKeyOffline() {
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
    }
  ];

  await generateKey(aliasString);
  await huks.anonAttestKeyItemOffline(aliasString, properties);
}

```

