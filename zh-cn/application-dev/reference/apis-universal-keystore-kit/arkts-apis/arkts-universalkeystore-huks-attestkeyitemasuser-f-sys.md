# attestKeyItemAsUser（系统接口）

## attestKeyItemAsUser

```TypeScript
function attestKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<HuksReturnResult>
```

ָ���û����ݻ�ȡ��Կ֤�飬ʹ��Promise��ʽ�첽���ؽ����

**起始版本：** 12

**需要权限：** ohos.permission.ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | �û�ID�� |
| keyAlias | string | 是 | ��Կ��������Ŵ���ȡ֤����Կ�ı����� |
| huksOptions | HuksOptions | 是 | ���ڻ�ȡ֤��ʱָ��������������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksReturnResult&gt; | Promise���󡣵����óɹ�ʱ��HuksReturnResult��certChains��Ա�ǿգ�Ϊ��ȡ����֤����������Ϊʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application permission is not sufficient, which may be caused by lack of<br/><br/>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-nonsystem) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-Feature) | Feature is not supported. Possible causes:<br/>1. The algorithm mode is not supported.<br/>2. The group key is not supported.<br/>3. The crypto extension key is not supported. |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |

**示例：**

以下代码示例接口调用的前置条件同上文[generateKeyItemAsUser](#huksgeneratekeyitemasuser)的前置条件

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const rsaKeyAlias = 'test_rsaKeyAlias';
const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;

const securityLevel = StringToUint8Array('sec_level');
const challenge = StringToUint8Array('challenge_data');
const versionInfo = StringToUint8Array('version_info');

function GetRSA4096GenerateProperties(): Array<huks.HuksParam> {
  return [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_4096
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: userIdStorageLevel,
  }]
}

async function GenerateKey(keyAlias: string, genProperties: Array<huks.HuksParam>) {
  const options: huks.HuksOptions = {
    properties: genProperties
  }
  await huks.generateKeyItemAsUser(userId, keyAlias, options).then((data) => {
    console.info("成功生成了一个别名为：" + keyAlias + " 的密钥")
  }).catch((err: BusinessError) => {
    console.error("密钥生成失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

function GetAttestKeyProperties(keyAlias: string): Array<huks.HuksParam> {
  return new Array<huks.HuksParam>({
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO,
    value: securityLevel
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
    value: challenge
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_VERSION_INFO,
    value: versionInfo
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
    value: StringToUint8Array(keyAlias)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: userIdStorageLevel,
  })
}

async function LetKeyAttest(keyAlias: string, keyOptions: Array<huks.HuksParam>) {
  let attestOptions: huks.HuksOptions = {
    properties: keyOptions,
  }
  console.info('开始attest')
  await huks.attestKeyItemAsUser(userId, keyAlias, attestOptions).then((data) => {
    console.info('attestation ok!')
    console.debug(`拿到的证书链是${JSON.stringify(data)}`) // 这里是调试信息，实际业务功能开发无需打印证书链。
    for (let i = 0; data?.certChains?.length && i < data?.certChains?.length; ++i) {
      console.debug(`证书${i}是${data.certChains[i]}`) // 这里是调试信息，实际业务功能开发无需打印证书链。
    }
    console.info("attest 成功")
  }).catch((err: BusinessError) => {
    console.error("attest 失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

async function TestHuksAttest() {
  await GenerateKey(rsaKeyAlias, GetRSA4096GenerateProperties())
  await LetKeyAttest(rsaKeyAlias, GetAttestKeyProperties(rsaKeyAlias))
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  TestHuksAttest()
}

```

