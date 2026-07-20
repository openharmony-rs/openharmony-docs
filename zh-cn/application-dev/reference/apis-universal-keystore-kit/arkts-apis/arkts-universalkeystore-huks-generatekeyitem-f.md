# generateKeyItem

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="generatekeyitem"></a>
## generateKeyItem

```TypeScript
function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void
```

生成密钥。使用callback异步回调。

基于密钥不出[TEE](docroot://security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。

> **说明：**  
>  
> 生成[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥需要ohos.permission.ACCESS_SE_KEY权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void--><!--Device-huks-function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名。密钥别名的最大长度为128字节，建议不包含个人信息等敏感词汇。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于存放生成key所需TAG。其中密钥使用的算法、密钥用途、密钥长度为必选参数。指定[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别时，需要ohos.permission.ACCESS_SE_KEY权限。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当生成密钥成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The queried entity does not exist. This may happen because the key resource ID specified by keyAlias has not been opened in the external crypto scenario.<br>**适用版本：** 26.0.0+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 26.0.0+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 26.0.0+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 26.0.0+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 26.0.0+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

ArkTS示例：

```TypeScript
/* 以生成ECC密钥为例 */
import { huks } from '@kit.UniversalKeystoreKit';

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
/* 生成密钥 */
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


<a id="generatekeyitem-1"></a>
## generateKeyItem

```TypeScript
function generateKeyItem(keyAlias: string, options: HuksOptions): Promise<void>
```

生成密钥。使用Promise异步回调。

基于密钥不出[TEE](docroot://security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。

> **说明：**  
>  
> 生成[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别密钥需要ohos.permission.ACCESS_SE_KEY权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function generateKeyItem(keyAlias: string, options: HuksOptions): Promise<void>--><!--Device-huks-function generateKeyItem(keyAlias: string, options: HuksOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名。密钥别名的最大长度为128字节，建议不包含个人信息等敏感词汇。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于存放生成key所需TAG。其中密钥使用的算法、密钥用途、密钥长度为必选参数。指定[HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)中定义的SE安全级别时，需要ohos.permission.ACCESS_SE_KEY权限。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application permissions are insufficient, possibly because the ohos.permission.ACCESS_SE_KEY permission is missing.<br>**适用版本：** 26.0.0+ |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000001](../errorcode-huks.md#12000001-该子功能不支持特性) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-缺少密钥算法参数) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-无效的密钥算法参数) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-密钥设置生物访问控制时待绑定的凭据不存在) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-调用其他系统服务失败) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-同名密钥已存在) | The key with the same alias already exists<br>**适用版本：** 20+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000011](../errorcode-huks.md#12000011-目标对象不存在) | The queried entity does not exist. This may happen because the key resource ID specified by keyAlias has not been opened in the external crypto scenario.<br>**适用版本：** 26.0.0+ |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 26.0.0+ |
| [12000021](../errorcode-huks.md#12000021-ukey-pin码被锁定) | the UKey PIN is locked<br>**适用版本：** 26.0.0+ |
| [12000023](../errorcode-huks.md#12000023-ukey-pin码未认证) | the UKey PIN not authenticated<br>**适用版本：** 26.0.0+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 26.0.0+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
/* 以生成ECC密钥为例 */
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
/* 生成密钥 */
huks.generateKeyItem(keyAlias, options)
  .then((data) => {
    console.info(`promise: generateKeyItem success`);
  });

```

