# generateKey

## generateKey

```TypeScript
function generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

������Կ��ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.generateKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-generatekeyitem-f.md#generateKeyItem-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** generateKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڴ������key����TAG�� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص���������������Կ�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以生成RSA512密钥为例 */

let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_512
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  },
  {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }
];
let options: huks.HuksOptions = {
  properties: properties
};
huks.generateKey(keyAlias, options, (err, data) => {
});

```


## generateKey

```TypeScript
function generateKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

������Կ��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.generateKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-generatekeyitem-f.md#generateKeyItem-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** generateKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڴ������key����TAG�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以生成ECC256密钥为例 */

let keyAlias = 'keyAlias';
let properties: Array<huks.HuksParam> = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_ECC
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  },
  {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }
];
let options: huks.HuksOptions = {
  properties: properties
};
let result = huks.generateKey(keyAlias, options);

```

