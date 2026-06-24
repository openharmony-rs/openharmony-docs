# initSessionAsUser（系统接口）

## initSessionAsUser

```TypeScript
function initSessionAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<HuksSessionHandle>
```

ָ���û����ݲ�����Կ�ӿڣ�ʹ��Promise��ʽ�첽���ؽ����huks.initSessionAsUser, huks.updateSession, huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | �û�ID�� |
| keyAlias | string | 是 | initSessionAsUser������Կ�ı����� |
| huksOptions | HuksOptions | 是 | initSessionAsUser�������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksSessionHandle&gt; | Promise���󡣽�initSessionAsUser�������ص�handle���ӵ���Կ����ϵͳ�Ļص��� |

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
| [12000010](../../errorcode-universal.md#12000010-the) | the number of sessions has reached limit |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |

**示例：**

注意：下文密码学相关的变量（如initializationVector）赋值，均为参考样例，不能直接适用于业务功能逻辑。开发者需要根据自身场景使用合适的初始值。

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

const aesKeyAlias = 'test_aesKeyAlias';
const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;
const initializationVector = '001122334455';
const plainText = '123456789';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

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

function GetAesEncryptProperties(): Array<huks.HuksParam> {
  return [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: StringToUint8Array(initializationVector)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: userIdStorageLevel,
  }]
}

function GetAesDecryptProperties(): Array<huks.HuksParam> {
  return [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: StringToUint8Array(initializationVector)
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

async function EncryptData(keyAlias: string, encryptProperties: Array<huks.HuksParam>): Promise<Uint8Array> {
  const options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: StringToUint8Array(plainText)
  }
  let handle: number = 0;
  let cipherData: Uint8Array = new Uint8Array([]);
  await huks.initSessionAsUser(userId, keyAlias, options).then((data) => {
    handle = data.handle;
  }).catch((err: BusinessError) => {
    console.error("密钥初始化失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
  await huks.finishSession(handle, options).then((data) => {
    console.info("加密数据成功， 密文是： " + Uint8ArrayToString(data.outData))
    if (data.outData != undefined) {
      cipherData = data.outData
    }
    console.info("running time result success!")
  }).catch((err: BusinessError) => {
    console.error("加密流程捕获了异常，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
  return cipherData
}

async function DecryptData(keyAlias: string, decryptProperties: Array<huks.HuksParam>, cipherData: Uint8Array) {
  const options: huks.HuksOptions = {
    properties: decryptProperties,
    inData: cipherData
  }
  let handle: number = 0;
  await huks.initSessionAsUser(userId, keyAlias, options).then((data) => {
    handle = data.handle;
  }).catch((err: BusinessError) => {
    console.error("密钥初始化失败，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
  await huks.finishSession(handle, options).then((data) => {
    console.info("解密成功， 解密的明文是： " + Uint8ArrayToString(data.outData))
  }).catch((err: BusinessError) => {
    console.error("解密流程捕获了异常，错误码是： " + err.code + " 错误码信息： " + err.message)
  })
}

async function TestHuksInit() {
  await GenerateKey(aesKeyAlias, GetAesGenerateProperties())
  let cipherData: Uint8Array = await EncryptData(aesKeyAlias, GetAesEncryptProperties())
  await DecryptData(aesKeyAlias, GetAesDecryptProperties(), cipherData)
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  TestHuksInit()
}

```

