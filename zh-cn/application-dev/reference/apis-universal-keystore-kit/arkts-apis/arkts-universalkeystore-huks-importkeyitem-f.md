# importKeyItem

## importKeyItem

```TypeScript
function importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void
```

Imports a key in plaintext. This API uses an asynchronous callback to return the result.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Alias of the key. The value can contain up to 128 bytes and should not include<br/>sensitive data such as personal information. |
| options | HuksOptions | 是 | Tags required for the import and key to import. The algorithm, key purpose, and<br/>key length are mandatory. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. If the operation is successful,<br/>**err** is **undefined**. Otherwise, **err** is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist&lt;br&gt;**适用版本：** 9 - 19 |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000013](../../errorcode-universal.md#12000013-queried) | queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists&lt;br&gt;**适用版本：** 20+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以导入AES256密钥为例 */
let plainTextSize32 = makeRandomArr(32);

function makeRandomArr(size: number) {
  let arr = new Uint8Array(size);
  for (let i = 0; i < size; i++) {
    arr[i] = Math.floor(Math.random() * 10);
  }
  return arr;
};
let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value:
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }
];
let options: huks.HuksOptions = {
  properties: properties,
  inData: plainTextSize32
};
huks.importKeyItem(keyAlias, options, (error) => {
  if (error) {
    console.error(`callback: importKeyItem failed`);
  } else {
    console.info(`callback: importKeyItem success`);
  }
});

```


## importKeyItem

```TypeScript
function importKeyItem(keyAlias: string, options: HuksOptions): Promise<void>
```

Imports a key in plaintext. This API uses a promise to return the result.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Alias of the key. The value can contain up to 128 bytes and should not include<br/>sensitive data such as personal information. |
| options | HuksOptions | 是 | Tags required for the import and key to import. The algorithm, key purpose, and<br/>key length are mandatory. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000001](../../errorcode-universal.md#12000001-algorithm) | algorithm mode is not supported |
| [12000002](../../errorcode-universal.md#12000002-algorithm) | algorithm param is missing |
| [12000003](../../errorcode-universal.md#12000003-algorithm) | algorithm param is invalid |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist&lt;br&gt;**适用版本：** 9 - 19 |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000013](../../errorcode-universal.md#12000013-queried) | queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists&lt;br&gt;**适用版本：** 20+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以导入AES256为例 */
function makeRandomArr(size: number) {
  let arr = new Uint8Array(size);
  for (let i = 0; i < size; i++) {
    arr[i] = Math.floor(Math.random() * 10);
  }
  return arr;
};

/* 第一步：生成密钥 */
let plainTextSize32 = makeRandomArr(32);
let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }
];
let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: plainTextSize32
};
/* 第二步：导入密钥 */
huks.importKeyItem(keyAlias, huksOptions)
  .then(() => {
    console.info(`promise: importKeyItem success`);
  });

```

