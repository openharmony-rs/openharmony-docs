# hasKeyItemAsUser（系统接口）

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="haskeyitemasuser"></a>
## hasKeyItemAsUser

```TypeScript
function hasKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<boolean>
```

指定用户身份判断密钥是否存在，使用Promise回调异步返回结果。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-huks-function hasKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<boolean>--><!--Device-huks-function hasKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG，如使用[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md)指定需查询密钥的安全级别，<br>可传空，当API version ≥12时，传空默认为CE，当API version ＜ 12时，传空默认为DE。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。若密钥存在，返回值为true，若密钥不存在，返回值为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application permission is not sufficient, which may be caused by lack of<br>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Feature is not supported. Possible causes:1. The group key is not supported.2. The crypto extension key is not supported.<br>**适用版本：** 23+ |

**示例：**

以下代码示例接口调用的前置条件同上文[generateKeyItemAsUser](#huksgeneratekeyitemasuser)的前置条件

```TypeScript
/* 以查询AES密钥是否存在为例 */
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
    console.info("成功生成了一个别名为：" + keyAlias + " 的密钥")
  }).catch((err: BusinessError) => {
    console.error("密钥生成失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

/* 2. 查询密钥是否存在 */
async function HasKey(keyAlias: string) {
  const options: huks.HuksOptions = {
    properties: [{
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }]
  }
  await huks.hasKeyItemAsUser(userId, keyAlias, options).then((data) => {
    console.info("别名为: " + keyAlias + "的密钥查询存在结果" + JSON.stringify(data))
  }).catch((err: BusinessError) => {
    console.error("密钥查询失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

async function TestHuksHasKey() {
  await GenerateKey(aesKeyAlias, GetAesGenerateProperties())
  await HasKey(aesKeyAlias)
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  TestHuksHasKey()
}

```

