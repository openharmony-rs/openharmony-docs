# deleteKeyItemAsUser（系统接口）

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="deletekeyitemasuser"></a>
## deleteKeyItemAsUser

```TypeScript
function deleteKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>
```

指定用户身份删除密钥，使用Promise方式异步返回结果。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-huks-function deleteKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>--><!--Device-huks-function deleteKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| keyAlias | string | 是 | 密钥别名，应为生成key时传入的别名。 |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于删除时指定密钥的属性TAG，如使用[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md)指定需删除密钥的安全级别，<br>可传空，当API version ≥12时，传空默认为CE，当API version ＜ 12时，传空默认为DE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application permission is not sufficient, which may be caused by lack of<br>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system applications are not allowed to use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Feature is not supported. Possible causes:1. The group key is not supported.2. The crypto extension key is not supported.<br>**适用版本：** 23+ |

**示例：**

以下代码示例接口调用的前置条件同上文[generateKeyItemAsUser](#huksgeneratekeyitemasuser)的前置条件

```TypeScript
/* 以删除AES密钥为例 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
/* 1. 生成密钥 */
async function GenerateKey(keyAlias: string, genProperties: Array<huks.HuksParam>) {
  const options: huks.HuksOptions = {
    properties: genProperties
  }
  await huks.generateKeyItemAsUser(userId, keyAlias, options).then((data) => {
  }).catch((err: BusinessError) => {
    console.error("密钥生成失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}
/* 2. 删除密钥 */
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

