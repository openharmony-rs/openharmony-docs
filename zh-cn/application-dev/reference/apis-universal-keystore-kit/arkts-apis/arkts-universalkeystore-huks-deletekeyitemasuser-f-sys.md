# deleteKeyItemAsUser（系统接口）

## deleteKeyItemAsUser

```TypeScript
function deleteKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>
```

ָ���û�����ɾ����Կ��ʹ��Promise��ʽ�첽���ؽ����

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | �û�ID�� |
| keyAlias | string | 是 | ��Կ������ӦΪ����keyʱ����ı����� |
| huksOptions | HuksOptions | 是 | ����ɾ��ʱָ����Կ������TAG����ʹ��<br/>[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ����ɾ����Կ�İ�ȫ����<br/>�ɴ��գ���API version ��<br/>12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-the) | the application permission is not sufficient, which may be caused by lack of<br/><br/>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-nonsystem) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000001](../../errorcode-universal.md#12000001-Feature) | Feature is not supported. Possible causes:<br/>1. The group key is not supported.<br/>2. The crypto extension key is not supported.&lt;br&gt;**适用版本：** 23+ |

**示例：**

以下代码示例接口调用的前置条件同上文[generateKeyItemAsUser](#huksgeneratekeyitemasuser)的前置条件

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

const aesKeyAlias = 'test_aesKeyAlias';
const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;

function GetAesGenerateProperties(): Array<huks.HuksParam> {
  return [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
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
  }).catch((err: BusinessError) => {
    console.error("密钥生成失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

async function DeleteKey(keyAlias: string) {
  const options: huks.HuksOptions = {
    properties: [{
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }]
  }
  await huks.deleteKeyItemAsUser(userId, keyAlias, options).then((data) => {
    console.info("别名为: " + keyAlias + " 密钥删除成功！")
  }).catch((err: BusinessError) => {
    console.error("密钥删除失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

async function TestHuksDelete() {
  await GenerateKey(aesKeyAlias, GetAesGenerateProperties())
  await DeleteKey(aesKeyAlias)
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  TestHuksDelete()
}

```

