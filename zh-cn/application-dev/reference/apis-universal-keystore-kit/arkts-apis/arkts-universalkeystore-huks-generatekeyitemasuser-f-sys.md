# generateKeyItemAsUser（系统接口）

## generateKeyItemAsUser

```TypeScript
function generateKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<void>
```

ָ���û�����������Կ��ʹ��Promise��ʽ�첽���ؽ����������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ��ͨ��
promise���᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | �û�ID�� |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| huksOptions | HuksOptions | 是 | ���ڴ������key�����<br/>[���Ա�ǩ](../../../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#ö��)��������Կʹ�õ��㷨����Կ��;����Կ����Ϊ��ѡ������ |

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
| [12000001](../../errorcode-universal.md#12000001-Feature) | Feature is not supported. Possible causes:<br/>1. The algorithm mode is not supported.<br/>2. The group key is not supported.<br/>3. The crypto extension key is not supported. |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000013](../../errorcode-universal.md#12000013-queried) | queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists&lt;br&gt;**适用版本：** 20+ |

**示例：**

调用方必须是运行在User0~99（包含0和99）用户身份下的系统应用，同时需要申请ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。允许应用安装到User0的配置指导，请参考[singleton|bool|false|是否允许应用安装到单用户下(U0)](../../../../zh-cn/device-dev/subsystems/subsys-app-privilege-config-guide.md#可由设备厂商配置的特权)

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
    console.info("成功生成了一个别名为：" + keyAlias + " 的密钥")
  }).catch((err: BusinessError) => {
    console.error("密钥生成失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}


export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  GenerateKey(aesKeyAlias, GetAesGenerateProperties())
}

```

