# generateKeyItem

## generateKeyItem

```TypeScript
function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void
```

������Կ��ʹ��callback�첽�ص���

������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ�򣬴˽ӿڲ��᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڴ������key����TAG��������Կʹ�õ��㷨����Կ��;����Կ����Ϊ��ѡ������ |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������������Կ�ɹ�ʱ��errΪundefined������Ϊ������� |

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
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000013](../../errorcode-universal.md#12000013-queried) | queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists&lt;br&gt;**适用版本：** 20+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000011](../../errorcode-universal.md#12000011-The) | The queried entity does not exist. This may happen because<br/>the key resource ID specified by keyAlias has not been opened in the external crypto scenario.&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

ArkTS示例：

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 以生成ECC256密钥为例 */
let keyAlias: string = 'keyAlias';
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
  },
];
let options: huks.HuksOptions = {
  properties: properties
};
huks.generateKeyItem(keyAlias, options, (error) => {
  if (error) {
    console.error(`callback: generateKeyItem failed`);
  } else {
    console.info(`callback: generateKeyItem key success`);
  }
});

```

JS示例代码仅供轻量级设备使用。

```TypeScript
<stack class="container">
    <input type="button" class="generateBtn" @click="generateKey">生成密钥</input>
    <text class="result">{{result}}</text>
</stack>

```

```TypeScript
.container {
  width: 454px;
  height: 800px;
  background-color: #ffffffff;
}

.generateBtn {
  left: 77px;
  top: 100px;
  width: 300px;
  height: 80px;
  text-align: center;
  color: white;
  background-color: orange;
  font-size: 25px;
}

.result {
  left: 30px;
  top: 190px;
  width: 390px;
  height: 80px;
  text-align: center;
  color: #ff000000;
  background-color: #ffffffff;
  font-size: 25px;
}

```

```TypeScript
import huks from '@ohos.security.huks';

function testGenerateKey() {
    let huksInfo;
    let keyAlias = 'keyAlias';
    let properties = [{
        tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
        value: huks.HuksKeyAlg.HUKS_ALG_DES
    }, {
        tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
        value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
    }, {
        tag: huks.HuksTag.HUKS_TAG_PURPOSE,
        value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
        huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
    }];
    let options = {
        properties: properties
    };

    huks.generateKeyItem(keyAlias, options, (err) => {
        if (err) {
            huksInfo = 'generateKeyItem failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
        } else {
            huksInfo = 'generateKeyItem succeeded';
            console.info(huksInfo);
        }
    });
    return huksInfo;
}

export default {
    data: {
        result: ''
    },

    generateKey() {
        this.result = testGenerateKey();
    }
};

```


## generateKeyItem

```TypeScript
function generateKeyItem(keyAlias: string, options: HuksOptions): Promise<void>
```

������Կ��ʹ��Promise�첽�ص���

������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ�򣬴˽ӿڲ��᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ��������Կ��������󳤶�Ϊ128�ֽڣ����鲻����������Ϣ�����дʻ㡣 |
| options | HuksOptions | 是 | ���ڴ������key����TAG��������Կʹ�õ��㷨����Կ��;����Կ����Ϊ��ѡ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

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
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000013](../../errorcode-universal.md#12000013-queried) | queried credential does not exist |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000015](../../errorcode-universal.md#12000015-Failed) | Failed to obtain the security information via UserIAM |
| [12000017](../../errorcode-universal.md#12000017-The) | The key with the same alias already exists&lt;br&gt;**适用版本：** 20+ |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |
| [12000011](../../errorcode-universal.md#12000011-The) | The queried entity does not exist. This may happen because<br/>the key resource ID specified by keyAlias has not been opened in the external crypto scenario.&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000020](../../errorcode-universal.md#12000020-the) | the provider operation failed&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000021](../../errorcode-universal.md#12000021-the) | the UKey PIN is locked&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000023](../../errorcode-universal.md#12000023-the) | the UKey PIN not authenticated&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000024](../../errorcode-universal.md#12000024-the) | the provider or UKey is busy&lt;br&gt;**适用版本：** 26.0.0+ |
| [12000026](../../errorcode-universal.md#12000026-the) | the secure element is not available&lt;br&gt;**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
/* 以生成ECC256密钥为例 */
import { huks } from '@kit.UniversalKeystoreKit';

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
  },
];
let options: huks.HuksOptions = {
  properties: properties
};
huks.generateKeyItem(keyAlias, options)
  .then((data) => {
    console.info(`promise: generateKeyItem success`);
  });

```

