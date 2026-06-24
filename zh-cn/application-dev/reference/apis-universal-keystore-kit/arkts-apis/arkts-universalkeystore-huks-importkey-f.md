# importKey

## importKey

```TypeScript
function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

����������Կ��ʹ��Callback��ʽ�ص��첽���ؽ����

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.importKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-importkeyitem-f.md#importKeyItem-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** importKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڵ���ʱ����TAG����Ҫ�������Կ�� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص���������������Կ�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |

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

����������Կ��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.importKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-importkeyitem-f.md#importKeyItem-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** importKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڵ���ʱ����TAG����Ҫ�������Կ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

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
/* 第二步：导入密钥 */
let result = huks.importKey(keyAlias, huksOptions);

```

