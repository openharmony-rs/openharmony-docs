# importWrappedKeyItemAsUser（系统接口）

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="importwrappedkeyitemasuser"></a>
## importWrappedKeyItemAsUser

```TypeScript
function importWrappedKeyItemAsUser(
    userId: number, keyAlias: string,
    wrappingKeyAlias: string,
    huksOptions: HuksOptions
  ): Promise<void>
```

Import Wrapped Key As User.

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-huks-function importWrappedKeyItemAsUser(
    userId: number, keyAlias: string,
    wrappingKeyAlias: string,
    huksOptions: HuksOptions
  ): Promise<void>--><!--Device-huks-function importWrappedKeyItemAsUser(
    userId: number, keyAlias: string,
    wrappingKeyAlias: string,
    huksOptions: HuksOptions
  ): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | User ID. |
| keyAlias | string | 是 | Alias of the wrapped key to import. |
| wrappingKeyAlias | string | 是 | Alias of the key used to decrypt the wrapped key. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Options for importing the wrapped key. The algorithm, key purpose, and key length are mandatory. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application permission is not sufficient, which may be caused by lack of<br>cross-account permission, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system applications are not allowed to use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | Feature is not supported. Possible causes:1. The algorithm mode is not supported.2. The group key is not supported.3. The crypto extension key is not supported. |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |

**示例：**

注意：下文密码学相关的变量（如initializationVector、associatedData、nonce）赋值，均为参考样例，不能直接适用于业务功能逻辑。开发者需要根据自身场景使用合适的初始值。

```TypeScript
/* 以ECDH协商安全导入AES密钥为例 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;
const initializationVector = '0000000000000000';
const associatedData = "abababababababab";
const nonce = "hahahahahaha";
const tagSize = 16;
const unsignedInt32Bytes = 4;
const importedAes192PlainKey = "The aes192 key to import";
const callerAes256Kek = "This is kek to encrypt aes192 key";
const callerKeyAlias = "test_caller_key_ecdh_aes192";
const callerKekAliasAes256 = "test_caller_kek_ecdh_aes256";
const callerAgreeKeyAliasAes256 = "test_caller_agree_key_ecdh_aes256";
const importedKeyAliasAes192 = "test_import_key_ecdh_aes192";
const mask = [0x000000FF, 0x0000FF00, 0x00FF0000, 0xFF000000];


function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function SubUint8ArrayOf(arrayBuf: Uint8Array, start: number, end: number) {
  let arr: Array<number> = [];
  for (let i = start; i < end && i < arrayBuf.length; ++i) {
    arr.push(arrayBuf[i]);
  }
  return new Uint8Array(arr);
}

function AssignLength(length: number, arrayBuf: Uint8Array, startIndex: number) {
  let index = startIndex;
  for (let i = 0; i < 4; i++) {
    arrayBuf[index++] = (length & mask[i]) >> (i * 8);
  }
  return 4;
}

function AssignData(data: Uint8Array, arrayBuf: Uint8Array, startIndex: number) {
  let index = startIndex;
  for (let i = 0; i < data.length; i++) {
    arrayBuf[index++] = data[i];
  }
  return data.length;
}

const genWrappingKeyParams: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_ECC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_UNWRAP
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

const genCallerEcdhParams: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_ECC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_CURVE25519_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

const importParamsCallerKek: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_AES
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_GCM
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_IV,
      value: stringToUint8Array(initializationVector)
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ],
  inData: stringToUint8Array(callerAes256Kek)
}

const importParamsAgreeKey: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_AES
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_GCM
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_IV,
      value: stringToUint8Array(initializationVector)
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

const callerAgreeParams: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_ECDH
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_CURVE25519_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

const encryptKeyCommonParams: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_AES
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_GCM
    },
    {
      tag: huks.HuksTag.HUKS_TAG_NONCE,
      value: stringToUint8Array(nonce)
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ASSOCIATED_DATA,
      value: stringToUint8Array(associatedData)
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

const importWrappedAes192Params: huks.HuksOptions = {
  properties: [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_AES
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
      huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_192
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_CBC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_UNWRAP_ALGORITHM_SUITE,
      value: huks.HuksUnwrapSuite.HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING
    },
    {
      tag: huks.HuksTag.HUKS_TAG_IV,
      value: stringToUint8Array(initializationVector)
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ]
}

/* 明文导入密钥 */
async function PublicImportKeyItemFunc(
  userId: number,
  keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`enter promise importKeyItemAsUser`);
  try {
    await huks.importKeyItemAsUser(userId, keyAlias, huksOptions)
      .then(data => {
        console.info(`promise: importKeyItemAsUser success, data = ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        console.error(`promise: importKeyItemAsUser failed, code: ${err.code}, msg: ${err.message}`);
      })
  } catch (err) {
    console.error(`promise: importKeyItemAsUser input arg invalid, code: ${err.code}, msg: ${err.message}`);
  }
}

/* 删除密钥 */
async function PublicDeleteKeyItemFunc(
  userId: number,
  keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`enter promise deleteKeyItemAsUser`);
  try {
    await huks.deleteKeyItemAsUser(userId, keyAlias, huksOptions)
      .then(data => {
        console.info(`promise: deleteKeyItemAsUser key success, data = ${JSON.stringify(data)}`);
      })
      .catch((err: BusinessError) => {
        console.error(`promise: deleteKeyItemAsUser failed, code: ${err.code}, msg: ${err.message}`);
      })
  } catch (err) {
    console.error(`promise: deleteKeyItemAsUser input arg invalid, code: ${err.code}, msg: ${err.message}`);
  }
}

/* 安全导入密钥 */
async function PublicImportWrappedKeyFunc(
  userId: number,
  keyAlias: string, wrappingKeyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`enter callback importWrappedKeyItemAsUser`);
  console.info(`publicImportWrappedKeyFunc huksOptions = ${JSON.stringify(huksOptions)}`);
  try {
    await huks.importWrappedKeyItemAsUser(userId, keyAlias, wrappingKeyAlias, huksOptions)
      .then((data) => {
        console.info(`callback: importWrappedKeyItemAsUser success, data = ${JSON.stringify(data)}`);
        console.info(`importWrappedKeyItemAsUser 成功 data = ${JSON.stringify(data)}`)
      })
      .catch((err: BusinessError) => {
        console.error(`callback: importWrappedKeyItemAsUser failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (error) {
    console.error(`callback: importWrappedKeyItemAsUser input arg invalid, code: ${error.code}, msg: ${error.message}`);
  }
}

/* 初始化密钥会话 */
async function PublicInitFunc(
  userId: number,
  srcKeyAlias: string, huksOptions: huks.HuksOptions) {
  let handle: number = 0;
  console.info(`enter promise doInit`);
  try {
    await huks.initSessionAsUser(userId, srcKeyAlias, huksOptions)
      .then((data) => {
        console.info(`promise: initSessionAsUser success, data = ${JSON.stringify(data)}`);
        handle = data.handle;
      })
      .catch((err: BusinessError) => {
        console.error(`promise: initSessionAsUser key failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (error) {
    console.error(`promise: doInit input arg invalid, code: ${error.code}, msg: ${error.message}`);
  }
  return handle;
}

/* 分段更新会话数据 */
async function PublicUpdateSessionFunction(handle: number, huksOptions: huks.HuksOptions) {
  if (huksOptions?.inData?.length == undefined) {
    return [];
  }
  const maxUpdateSize = 64;
  const inData = huksOptions.inData;
  const lastInDataPosition = inData.length - 1;
  let inDataSegSize = maxUpdateSize;
  let inDataSegPosition = 0;
  let isFinished = false;
  let outData: Array<number> = [];

  while (inDataSegPosition <= lastInDataPosition) {
    if (inDataSegPosition + maxUpdateSize > lastInDataPosition) {
      isFinished = true;
      inDataSegSize = lastInDataPosition - inDataSegPosition + 1;
      console.info(`enter promise doUpdate`);
      break;
    }
    huksOptions.inData = new Uint8Array(
      Array.from(inData).slice(inDataSegPosition, inDataSegPosition + inDataSegSize)
    );
    console.info(`enter promise doUpdate`);
    try {
      await huks.updateSession(handle, huksOptions)
        .then((data) => {
          console.info(`promise: doUpdate success, data = ${JSON.stringify(data)}`);
          if (data.outData == undefined) {
            console.error('data.outData is undefined');
            return;
          }
          outData = outData.concat(Array.from(data.outData));
        })
        .catch((err: BusinessError) => {
          console.error(`promise: doUpdate failed, code: ${err.code}, msg: ${err.message}`);
        });
    } catch (error) {
      console.error(`promise: doUpdate input arg invalid, code: ${error.code}, msg: ${error.message}`);
    }
    if ((!isFinished) && (inDataSegPosition + maxUpdateSize > lastInDataPosition)) {
      console.error(`update size invalid isFinished = ${isFinished}`);
      console.error(`inDataSegPosition = ${inDataSegPosition}`);
      console.error(`lastInDataPosition = ${lastInDataPosition}`);
      return [];
    }
    inDataSegPosition += maxUpdateSize;
  }
  return outData;
}

/* 结束密钥会话并进行相应的密钥操作 */
async function PublicFinishSession(handle: number, huksOptions: huks.HuksOptions, inData: Array<number>) {
  let outData: Array<number> = [];
  console.info(`enter promise doFinish`);
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        console.info(`promise: doFinish success, data = ${JSON.stringify(data)}`);
        if (data.outData == undefined) {
          console.error('data.outData is undefined');
          return;
        }
        outData = inData.concat(Array.from(data.outData));
      })
      .catch((err: BusinessError) => {
        console.error(`promise: doFinish key failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (error) {
    console.error(`promise: doFinish input arg invalid, code: ${error.code}, msg: ${error.message}`);
  }
  return new Uint8Array(outData);
}

/* 进行数据加密 */
async function CipherFunction(
  userId: number,
  keyAlias: string, huksOptions: huks.HuksOptions) {
  const handle = await PublicInitFunc(userId, keyAlias, huksOptions);
  const tmpData = await PublicUpdateSessionFunction(handle, huksOptions);
  const outData = await PublicFinishSession(handle, huksOptions, tmpData);
  return outData;
}

/* 进行ECDH协商 */
async function AgreeFunction(
  userId: number,
  keyAlias: string, huksOptions: huks.HuksOptions, huksPublicKey: Uint8Array) {
  const handle = await PublicInitFunc(userId, keyAlias, huksOptions);
  let outSharedKey: Uint8Array = new Uint8Array;
  huksOptions.inData = huksPublicKey;
  console.info(`enter promise doUpdate`);
  try {
    await huks.updateSession(handle, huksOptions)
      .then((data) => {
        console.info(`promise: doUpdate success, data = ${JSON.stringify(data)}`);
      })
      .catch((err: BusinessError) => {
        console.error(`promise: doUpdate failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (error) {
    console.error(`promise: doUpdate input arg invalid, code: ${error.code}, msg: ${error.message}`);
  }
  console.info(`enter promise doInit`);
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        console.info(`promise: doInit success, data = ${JSON.stringify(data)}`);
        if (data.outData == undefined) {
          console.error('data.outData is undefined');
          return;
        }
        outSharedKey = data.outData;
      })
      .catch((err: BusinessError) => {
        console.error(`promise: doInit key failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (error) {
    console.error(`promise: doInit input arg invalid, code: ${error.code}, msg: ${error.message}`);
  }
  return outSharedKey;
}

/* 导入KEK并协商共享密钥 */
async function ImportKekAndAgreeSharedSecret(
  userId: number,
  callerKekAlias: string, importKekParams: huks.HuksOptions,
  callerKeyAlias: string, huksPublicKey: Uint8Array, agreeParams: huks.HuksOptions) {
  await PublicImportKeyItemFunc(userId, callerKekAlias, importKekParams);

  importParamsAgreeKey.inData = await AgreeFunction(userId, callerKeyAlias, agreeParams, huksPublicKey);

  await PublicImportKeyItemFunc(userId, callerAgreeKeyAliasAes256, importParamsAgreeKey);
}

/* 生成密钥并导出公钥 */
async function GenerateAndExportPublicKey(
  userId: number,
  keyAlias: string, huksOptions: huks.HuksOptions): Promise<Uint8Array> {
  try {
    await huks.generateKeyItemAsUser(userId, keyAlias, huksOptions)
      .then(data => {
        console.info(`promise: generateKeyItemAsUser success, data = ${JSON.stringify(data)}`);
      })
      .catch((err: BusinessError) => {
        console.error(`callback: generateKeyItemAsUser failed, code: ${err.code}, msg: ${err.message}`);
      })
  } catch (err) {
    console.error(`callback: generateKeyItemAsUser invalid, code: ${err.code}, msg: ${err.message}`);
  }


  let result = new Uint8Array([])
  try {
    await huks.exportKeyItemAsUser(userId, keyAlias, huksOptions)
      .then((data) => {
        console.info(`promise: exportKeyItemAsUser success, data = ${JSON.stringify(data)}`);
        if (data.outData == undefined) {
          console.error('data.outData is undefined');
          return;
        }
        result = data.outData;
      })
      .catch((err: BusinessError) => {
        console.error(`promise: exportKeyItemAsUser failed, code: ${err.code}, msg: ${err.message}`);
      });
  } catch (e) {
    console.error(`promise: generate pubKey failed, code: ${e.code}, msg: ${e.message}`);
  }
  return result
}

interface KeyEncAndKekEnc {
  outPlainKeyEncData: Uint8Array,
  outKekEncData: Uint8Array,
  outKekEncTag: Uint8Array,
  outAgreeKeyEncTag: Uint8Array,
}

/* 加密待导入密钥和KEK */
async function EncryptImportedPlainKeyAndKek(
  userId: number,
  keyAlias: string): Promise<KeyEncAndKekEnc> {
  encryptKeyCommonParams.inData = stringToUint8Array(keyAlias)
  const plainKeyEncData = await CipherFunction(userId, callerKekAliasAes256, encryptKeyCommonParams);
  const result: KeyEncAndKekEnc = {
    outPlainKeyEncData: new Uint8Array([]),
    outKekEncData: new Uint8Array([]),
    outKekEncTag: new Uint8Array([]),
    outAgreeKeyEncTag: new Uint8Array([]),
  }
  result.outKekEncTag = SubUint8ArrayOf(plainKeyEncData, plainKeyEncData.length - tagSize, plainKeyEncData.length)
  result.outPlainKeyEncData = SubUint8ArrayOf(plainKeyEncData, 0, plainKeyEncData.length - tagSize)

  encryptKeyCommonParams.inData = stringToUint8Array(callerAes256Kek)
  const kekEncData = await CipherFunction(userId, callerAgreeKeyAliasAes256, encryptKeyCommonParams)
  result.outAgreeKeyEncTag = SubUint8ArrayOf(kekEncData, kekEncData.length - tagSize, kekEncData.length)
  result.outKekEncData = SubUint8ArrayOf(kekEncData, 0, kekEncData.length - tagSize)

  return result
}

/* 构建封装数据并安全导入密钥 */
async function BuildWrappedDataAndImportWrappedKey(plainKey: string, huksPubKey: Uint8Array,
  callerSelfPublicKey: Uint8Array, encData: KeyEncAndKekEnc) {
  const plainKeySizeBuff = new Uint8Array(4);
  AssignLength(plainKey.length, plainKeySizeBuff, 0);

  const wrappedData = new Uint8Array(
    unsignedInt32Bytes + huksPubKey.length +
      unsignedInt32Bytes + associatedData.length +
      unsignedInt32Bytes + nonce.length +
      unsignedInt32Bytes + tagSize +
      unsignedInt32Bytes + encData.outKekEncData.length +
      unsignedInt32Bytes + associatedData.length +
      unsignedInt32Bytes + nonce.length +
      unsignedInt32Bytes + tagSize +
      unsignedInt32Bytes + plainKeySizeBuff.length +
      unsignedInt32Bytes + encData.outPlainKeyEncData.length
  );
  let index = 0;
  const associatedDataArray = stringToUint8Array(associatedData);
  const nonceArray = stringToUint8Array(nonce);

  index += AssignLength(callerSelfPublicKey.length, wrappedData, index); // 4
  index += AssignData(callerSelfPublicKey, wrappedData, index); // 91
  index += AssignLength(associatedDataArray.length, wrappedData, index); // 4
  index += AssignData(associatedDataArray, wrappedData, index); // 16
  index += AssignLength(nonceArray.length, wrappedData, index); // 4
  index += AssignData(nonceArray, wrappedData, index); // 12
  index += AssignLength(encData.outAgreeKeyEncTag.length, wrappedData, index); // 4
  index += AssignData(encData.outAgreeKeyEncTag, wrappedData, index); // 16
  index += AssignLength(encData.outKekEncData.length, wrappedData, index); // 4
  index += AssignData(encData.outKekEncData, wrappedData, index); // 32
  index += AssignLength(associatedDataArray.length, wrappedData, index); // 4
  index += AssignData(associatedDataArray, wrappedData, index); // 16
  index += AssignLength(nonceArray.length, wrappedData, index); // 4
  index += AssignData(nonceArray, wrappedData, index); // 12
  index += AssignLength(encData.outKekEncTag.length, wrappedData, index); // 4
  index += AssignData(encData.outKekEncTag, wrappedData, index); // 16
  index += AssignLength(plainKeySizeBuff.length, wrappedData, index); // 4
  index += AssignData(plainKeySizeBuff, wrappedData, index); // 4
  index += AssignLength(encData.outPlainKeyEncData.length, wrappedData, index); // 4
  index += AssignData(encData.outPlainKeyEncData, wrappedData, index); // 24

  return wrappedData;
}

/* 安全导入密钥整体流程 */
export async function HuksSecurityImportTest(userId: number) {
  const srcKeyAliasWrap = 'HUKS_Basic_Capability_Import_0200';
  const huksPubKey: Uint8Array = await GenerateAndExportPublicKey(userId, srcKeyAliasWrap, genWrappingKeyParams);
  const callerSelfPublicKey: Uint8Array = await GenerateAndExportPublicKey(userId, callerKeyAlias, genCallerEcdhParams);

  await ImportKekAndAgreeSharedSecret(
    userId,
    callerKekAliasAes256, importParamsCallerKek, callerKeyAlias, huksPubKey, callerAgreeParams);
  const encData: KeyEncAndKekEnc = await EncryptImportedPlainKeyAndKek(userId, importedAes192PlainKey);
  const wrappedData =
    await BuildWrappedDataAndImportWrappedKey(importedAes192PlainKey, huksPubKey, callerSelfPublicKey, encData);
  importWrappedAes192Params.inData = wrappedData;
  await PublicImportWrappedKeyFunc(userId,
    importedKeyAliasAes192, srcKeyAliasWrap, importWrappedAes192Params);
  await PublicDeleteKeyItemFunc(userId, srcKeyAliasWrap, genWrappingKeyParams);
  await PublicDeleteKeyItemFunc(userId, callerKeyAlias, genCallerEcdhParams);
  await PublicDeleteKeyItemFunc(userId, importedKeyAliasAes192, importWrappedAes192Params);
  await PublicDeleteKeyItemFunc(userId, callerKekAliasAes256, callerAgreeParams);
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')

  const userId = 100;
  HuksSecurityImportTest(userId)
}

```

