# importKey

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## importKey

```TypeScript
function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

导入明文密钥，使用Callback方式回调异步返回结果。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.importKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-importkeyitem-f.md#importkeyitem)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [importKeyItem(keyAlias:](arkts-universalkeystore-huks-importkeyitem-f.md#importkeyitem)

<!--Device-huks-function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void--><!--Device-huks-function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名。密钥别名的最大长度为128字节，建议不包含个人信息等敏感词汇。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于导入时所需TAG和需要导入的密钥。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksResult&gt; | 是 | 回调函数。当导入密钥成功时，err为undefined，data为获取到的HuksResult；否则为错误对象。 |

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
huks.importKey(keyAlias, options, (err, data) => {
});

```


## importKey

```TypeScript
function importKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

导入明文密钥。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.importKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-importkeyitem-f.md#importkeyitem)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [importKeyItem(keyAlias:](arkts-universalkeystore-huks-importkeyitem-f.md#importkeyitem)

<!--Device-huks-function importKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>--><!--Device-huks-function importKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名。密钥别名的最大长度为128字节，建议不包含个人信息等敏感词汇。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于导入时所需TAG和需要导入的密钥。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise对象，返回HuksResult。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以导入AES128为例 */

function makeRandomArr(size: number) {
  let arr = new Uint8Array(size);
  for (let i = 0; i < size; i++) {
    arr[i] = Math.floor(Math.random() * 10);
  }
  return arr;
};

/* 1. 生成密钥 */
let plainTextSize32 = makeRandomArr(32);
let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
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
/* 2. 导入密钥 */
let result = huks.importKey(keyAlias, huksOptions);

```

