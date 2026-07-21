# abortSession

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="abortsession"></a>
## abortSession

```TypeScript
function abortSession(handle: number, options: HuksOptions, callback: AsyncCallback<void>): void
```

abortSession终止密钥操作。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function abortSession(handle: number, options: HuksOptions, callback: AsyncCallback<void>): void--><!--Device-huks-function abortSession(handle: number, options: HuksOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | abortSession操作的uint64类型的handle值。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | abortSession操作的参数集合。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当密钥操作abort成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

ArkTS示例：

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用，
 * 当这三个操作中的任一阶段发生错误时，都需要调用huks.abortSession来终止密钥的使用
 *
 * 以下以RSA密钥的callback功能使用为例
 */

let keyAlias = "HuksDemoRSA";
let properties: Array<huks.HuksParam> = []
let options: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(0)
};
let handle: number = 0;

async function huksAbort() {
  properties = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB,
  }];

  /* 1. 生成密钥 */
  huks.generateKeyItem(keyAlias, options, (error) => {
    if (error) {
      console.error(`callback: generateKeyItem failed`);
    } else {
      console.info(`callback: generateKeyItem success`);
      /* 2. 初始化密钥会话 */
      huks.initSession(keyAlias, options, (error, data) => { // 以initSession阶段进行abortSession为例
        if (error) {
          console.error(`callback: initSession failed`);
        } else {
          console.info(`callback: initSession success, data = ${JSON.stringify(data)}`);
          handle = data.handle;
          /* 3. 发生错误，终止密钥操作 */
          huks.abortSession(handle, options, (error) => {
            if (error) {
              console.error(`callback: abortSession failed`);
            } else {
              console.info(`callback: abortSession success`);
            }
          });
        }
      });
    }
  });
}

```

JS示例代码仅供轻量级设备使用。

```TypeScript
<stack class="container">
    <input type="button" class="threeStageBtn1" @click="threeStageEncrypt">加密数据</input>
    <input type="button" class="threeStageBtn2" @click="threeStageDecrypt">解密数据</input>
    <text class="result">{{result}}</text>
</stack>

```

```TypeScript
.container {
  width: 454px;
  height: 800px;
  background-color: #ffffffff;
}

.threeStageBtn1 {
  left: 77px;
  top: 100px;
  width: 300px;
  height: 80px;
  text-align: center;
  color: white;
  background-color: orange;
  font-size: 25px;
}

.threeStageBtn2 {
  left: 77px;
  top: 190px;
  width: 300px;
  height: 80px;
  text-align: center;
  color: white;
  background-color: orange;
  font-size: 25px;
}

.result {
  left: 30px;
  top: 280px;
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
import cryptoFramework from '@ohos.security.cryptoFramework';

/* huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用，
 * 当这三个操作中的任一阶段发生错误时，都需要调用huks.abortSession来终止密钥的使用
 *
 * 以下以使用DES/CBC/NoPadding加解密为例
 */

const keyAlias = 'keyAlias';
let handle;
let plainText = 'DESAAAdffssghCBC5612345612345L64';
let cipherText;
let IV = cryptoFramework.createRandom().generateRandomSync(8).data;

function stringToUint8Array(str) {
    let arr = [];
    for (let i = 0, j = str.length; i < j; ++i) {
        arr.push(str.charCodeAt(i));
    }
    return new Uint8Array(arr);
}

function uint8ArrayToString(fileData) {
    let dataString = '';
    for (let i = 0; i < fileData.length; i++) {
        dataString += String.fromCharCode(fileData[i]);
    }
    return dataString;
}

/* 加密参数集 */
function getDesEncryptProperties() {
    let properties = [{
        tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
        value: huks.HuksKeyAlg.HUKS_ALG_DES
    }, {
        tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
        value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
    }, {
        tag: huks.HuksTag.HUKS_TAG_PURPOSE,
        value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
    }, {
        tag: huks.HuksTag.HUKS_TAG_PADDING,
        value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    }, {
        tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
        value: huks.HuksCipherMode.HUKS_MODE_CBC
    }, {
        tag: huks.HuksTag.HUKS_TAG_IV,
        value: IV
    }];
    return properties;
}

/* 解密参数集 */
function getDesDecryptProperties() {
    let properties = [{
        tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
        value: huks.HuksKeyAlg.HUKS_ALG_DES
    }, {
        tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
        value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
    }, {
        tag: huks.HuksTag.HUKS_TAG_PURPOSE,
        value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
    }, {
        tag: huks.HuksTag.HUKS_TAG_PADDING,
        value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    }, {
        tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
        value: huks.HuksCipherMode.HUKS_MODE_CBC
    }, {
        tag: huks.HuksTag.HUKS_TAG_IV,
        value: IV
    }];
    return properties;
}

/* 1. 加密数据 */
function testThreeStageEncrypt() {
    let huksInfo;
    let ret = true;
    let initOptions = {
        properties: getDesEncryptProperties(),
        inData: new Uint8Array()
    };
    let updateOptions = {
        properties: getDesEncryptProperties(),
        inData: stringToUint8Array(plainText.substring(0, 16))
    };
    let finishOptions = {
        properties: getDesEncryptProperties(),
        inData: stringToUint8Array(plainText.substring(16, 32))
    };

    /* 2. 初始化加密会话 */
    huks.initSession(keyAlias, initOptions, (err, data) => {
        if (err) {
            huksInfo = 'encrypt initSession failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
            ret = false;
            huks.abortSession(data.handle, initOptions, (abortErr) => {
                if (abortErr) {
                    huksInfo = 'encrypt init abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                    console.error(huksInfo);
                }
            });
        } else {
            console.info('encrypt initSession succeeded');
            handle = data.handle;
        }
    });

    if (!ret) {
        return huksInfo;
    }

    huks.updateSession(handle, updateOptions, (err, data) => {
        if (err) {
            huksInfo = 'encrypt updateSession failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
            ret = false;
            huks.abortSession(handle, updateOptions, (abortErr) => {
                if (abortErr) {
                    huksInfo = 'encrypt update abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                    console.error(huksInfo);
                }
            });
        } else {
            console.info('encrypt updateSession succeeded');
            cipherText = uint8ArrayToString(data.outData);
            huksInfo = cipherText;
        }
    });
    
    if (!ret) {
        return huksInfo;
    }

    /* 3. 完成加密操作 */
    huks.finishSession(handle, finishOptions, (err, data) => {
        if (err) {
            huksInfo = 'encrypt finishSession failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
            huks.abortSession(handle, finishOptions, (abortErr) => {
                if (abortErr) {
                    huksInfo = 'encrypt finish abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                    console.error(huksInfo);
                }
            });
        } else {
            console.info('encrypt finishSession succeeded');
            cipherText = cipherText + uint8ArrayToString(data.outData);
            huksInfo = cipherText;
        }
    });
    return huksInfo;
}

/* 4. 解密数据 */
function testThreeStageDecrypt() {
    let huksInfo;
    let ret = true;
    let outPlainText;
    let initOptions = {
        properties: getDesDecryptProperties(),
        inData: new Uint8Array()
    };
    let updateOptions = {
        properties: getDesDecryptProperties(),
        inData: stringToUint8Array(cipherText.substring(0, 16))
    };
    let finishOptions = {
        properties: getDesDecryptProperties(),
        inData: stringToUint8Array(cipherText.substring(16, 32))
    };

    /* 5. 初始化解密会话 */
    huks.initSession(keyAlias, initOptions, (err, data) => {
        if (err) {
            huksInfo = 'decrypt initSession failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
            ret = false;
            huks.abortSession(handle, initOptions, (abortErr) => {
                if (abortErr) {
                    huksInfo = 'decrypt init abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                    console.error(huksInfo);
                }
            });
        } else {
            console.info('decrypt initSession succeeded');
            handle = data.handle;
        }
    });

    if (!ret) {
        return huksInfo;
    }

    huks.updateSession(handle, updateOptions, (err, data) => {
        if (err) {
            huksInfo = 'decrypt updateSession failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
            ret = false;
            huks.abortSession(handle, updateOptions, (abortErr) => {
                if (abortErr) {
                    huksInfo = 'decrypt update abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                    console.error(huksInfo);
                }
            });
        } else {
            console.info('decrypt updateSession succeeded');
            outPlainText = uint8ArrayToString(data.outData);
            huksInfo = outPlainText;
        }
    });

    /* 6. 完成解密操作 */
    huks.finishSession(handle, finishOptions, (err, data) => {
       if (err) {
           huksInfo = 'decrypt finishSession failed, code: ' + err.code + ', message: ' + err.message;
           console.error(huksInfo);
           huks.abortSession(handle, finishOptions, (abortErr) => {
               if (abortErr) {
                   huksInfo = 'decrypt finish abort failed, code: ' + abortErr.code + ', message: ' + abortErr.message;
                   console.error(huksInfo);
               }
           });
       } else {
           console.info('decrypt finishSession succeeded');
           outPlainText = outPlainText + uint8ArrayToString(data.outData);
           huksInfo = outPlainText;
       }
    });

    return huksInfo;
}

export default {
    data: {
        result: ''
    },

    threeStageEncrypt() {
        this.result = testThreeStageEncrypt();
    },

    threeStageDecrypt() {
        this.result = testThreeStageDecrypt();
    }
};

```


<a id="abortsession-1"></a>
## abortSession

```TypeScript
function abortSession(handle: number, options: HuksOptions): Promise<void>
```

abortSession终止密钥操作。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-huks-function abortSession(handle: number, options: HuksOptions): Promise<void>--><!--Device-huks-function abortSession(handle: number, options: HuksOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | abortSession操作的uint64类型的handle值。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | abortSession操作的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameter types.3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | api is not supported |
| [12000004](../errorcode-huks.md#12000004-文件错误) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-进程通信错误) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-算法库操作失败) | error occurred in crypto engine or UKey driver |
| [12000012](../errorcode-huks.md#12000012-外部错误) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-内存不足) | memory is insufficient |
| [12000020](../errorcode-huks.md#12000020-依赖的模块报错) | the provider operation failed<br>**适用版本：** 22+ |
| [12000024](../errorcode-huks.md#12000024-设备或资源繁忙) | the provider or UKey is busy<br>**适用版本：** 22+ |
| [12000018](../errorcode-huks.md#12000018-输入参数非法) | the group id specified by the access group tag is invalid<br>**适用版本：** 23+ |
| [12000026](../errorcode-huks.md#12000026-安全元件故障) | the secure element is not available<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用，
 * 当这三个操作中的任一阶段发生错误时，都需要调用huks.abortSession来终止密钥的使用
 *
 * 以下以RSA密钥的promise功能使用为例
 */
let keyAlias = "HuksDemoRSA";
let genProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB,
}];
let options: huks.HuksOptions = {
  properties: genProperties,
  inData: new Uint8Array(0)
};
let handle: number = 0;

/* 1. 生成密钥 */
async function generateKey() {
  await huks.generateKeyItem(keyAlias, options)
    .then(() => {
      console.info(`promise: generateKeyItem success`);
    });
}

/* 2. 初始化密钥会话 */
async function huksInit() {
  console.info('enter huksInit');
  await huks.initSession(keyAlias, options)
    .then((data) => {
      console.info(`promise: initSession success, data = ${JSON.stringify(data)}`);
      handle = data.handle;
    });
}

/* 3. 终止密钥会话 */
async function huksAbort() {
  console.info('enter huksAbort');
  await huks.abortSession(handle, options)
    .then(() => {
      console.info(`promise: abortSession success`);
    });
}

async function testAbort() {
  await generateKey();
  await huksInit(); // 以initSession阶段进行abortSession为例
  await huksAbort();
}

```

