# Md

Md类，调用Md方法进行消息摘要（Message Digest）计算。调用前，需要通过[createMd](arkts-cryptoarchitecture-cryptoframework-createmd-f.md#createmd-1)构造Md实例。

**起始版本：** 9

<!--Device-cryptoFramework-interface Md--><!--Device-cryptoFramework-interface Md-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="digest"></a>
## digest

```TypeScript
digest(callback: AsyncCallback<DataBlob>): void
```

返回Md的计算结果。使用callback异步回调。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-digest(callback: AsyncCallback<DataBlob>): void--><!--Device-Md-digest(callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataBlob&gt; | 是 | 回调函数。当摘要计算成功时，err为undefined，data为获取到的摘要结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function mdByCallback() {
  let md = cryptoFramework.createMd('SHA256');
  md.update({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) }, (err) => {
    md.digest((err, digestOutput) => {
      console.info('[Callback]: MD result: ' + digestOutput.data);
      console.info('[Callback]: MD len: ' + md.getMdLength());
    });
  });
}

```

<a id="digest-1"></a>
## digest

```TypeScript
digest(): Promise<DataBlob>
```

生成消息摘要。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-digest(): Promise<DataBlob>--><!--Device-Md-digest(): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回摘要计算结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

async function mdByPromise() {
  let md = cryptoFramework.createMd('SHA256');
  await md.update({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) });
  let mdOutput = await md.digest();
  console.info('[Promise]: MD result: ' + mdOutput.data);
  console.info('[Promise]: MD len: ' + md.getMdLength());
}

```

JS示例：

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="MdTest">Md异步测试</input>
</div>

```

```TypeScript
.container {
  width: 100%;
  height: 2000px;
  align-items: center;
  background-color: #fffefcfc;
  flex-direction: column;
  display: flex;
}

.TestTitle {
  width: 300px;
  height: 80px;
  text-align: center;
  background-color: white;
  color: #fff61515;
  font-size: 15fp;
}

.btn {
  width: 90%;
  height: 80px;
  text-align: center;
  background-color: #fff17f04;
  margin-top: 3px;
  color: white;
  font-size: 20fp;
}

```

```TypeScript
import cryptoFramework from '@ohos.security.cryptoFramework';

function StringToUint8Array(str) {
    let arr = [];
    for (let i = 0, j = str.length; i < j; ++i) {
        arr.push(str.charCodeAt(i));
    }
    return new Uint8Array(arr);
}

let plainText = "123456";

function mdTest() {
    let inData = StringToUint8Array(plainText);
    let md = cryptoFramework.createMd('SHA256');
    console.info("createMd " + typeof md);

    md.update({data: inData}, function (finishErr) {
        if (finishErr) {
            console.error("Digest update failed. Code:" + finishErr.code + " : " + finishErr.message);
        } else {
            console.info("Digest update successfully.");
        }
    })

    md.digest(function (finishErr, digestOutput){
        if (finishErr) {
            console.error("Digest failed. Code:" + finishErr.code + " : " + finishErr.message);
        } else {
            console.info("Digest successfully:" + digestOutput);
        }
    })
}

export default {
    data: {
        result: ''
    },
    MdTest() {
        mdTest();
    }
};

```

<a id="digestsync"></a>
## digestSync

```TypeScript
digestSync(): DataBlob
```

生成消息摘要，通过同步方式返回摘要计算结果。

<br><br>**说明：**<br>建议优先使用异步API{@link digest}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-digestSync(): DataBlob--><!--Device-Md-digestSync(): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.MessageDigest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 生成的消息摘要。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function mdBySync() {
  let md = cryptoFramework.createMd('SHA256');
  md.updateSync({ data: new Uint8Array(buffer.from('mdTestMessage', 'utf-8').buffer) });
  let mdOutput = md.digestSync();
  console.info('[Sync]: MD result: ' + mdOutput.data);
  console.info('[Sync]: MD len: ' + md.getMdLength());
}

```

JS示例：

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="MdTestSync">Md同步测试</input>
</div>

```

```TypeScript
.container {
  width: 100%;
  height: 2000px;
  align-items: center;
  background-color: #fffefcfc;
  flex-direction: column;
  display: flex;
}

.TestTitle {
  width: 300px;
  height: 80px;
  text-align: center;
  background-color: white;
  color: #fff61515;
  font-size: 15fp;
}

.btn {
  width: 90%;
  height: 80px;
  text-align: center;
  background-color: #fff17f04;
  margin-top: 3px;
  color: white;
  font-size: 20fp;
}

```

```TypeScript
import cryptoFramework from '@ohos.security.cryptoFramework';

function StringToUint8Array(str) {
    let arr = [];
    for (let i = 0, j = str.length; i < j; ++i) {
        arr.push(str.charCodeAt(i));
    }
    return new Uint8Array(arr);
}

function mdTestSync() {
    let mdAlgName = 'SHA256';
    let message = 'mdTestMessage';
    let md = cryptoFramework.createMd(mdAlgName);
    md.updateSync({ data: StringToUint8Array(message) });
    let mdResult = md.digestSync();
    console.info('Digest successfully. result:' + mdResult.data);
    let mdLen = md.getMdLength();
    console.info("Digest successfully. md len: " + mdLen);
}

export default {
    data: {
        result: ''
    },
    MdTestSync() {
        mdTestSync();
    }
};

```

<a id="getmdlength"></a>
## getMdLength

```TypeScript
getMdLength(): number
```

获取消息摘要的字节长度，单位为字节。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-getMdLength(): int--><!--Device-Md-getMdLength(): int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 消息摘要长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function getLength() {
  let md = cryptoFramework.createMd('SHA256');
  console.info('[Promise]: MD len: ' + md.getMdLength());
}

```

<a id="update"></a>
## update

```TypeScript
update(input: DataBlob, callback: AsyncCallback<void>): void
```

传入消息进行Md更新摘要状态。使用callback异步回调。update和digest为两段式接口，需要成组使用。其中digest必选，update可选。

> **说明：**  
>  
> Md算法多次调用update更新的代码示例详见开发指导  
> [分段摘要算法](docroot://security/CryptoArchitectureKit/crypto-generate-message-digest.md#分段摘要算法)。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-update(input: DataBlob, callback: AsyncCallback<void>): void--><!--Device-Md-update(input: DataBlob, callback: AsyncCallback<void>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 传入的消息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当摘要更新成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

<a id="update-1"></a>
## update

```TypeScript
update(input: DataBlob): Promise<void>
```

传入消息进行Md更新摘要状态。使用Promise异步回调。update和digest为两段式接口，需要成组使用。其中digest必选，update可选。

> **说明：**  
>  
> Md算法多次调用update更新的代码示例详见开发指导  
> [分段摘要算法](docroot://security/CryptoArchitectureKit/crypto-generate-message-digest.md#分段摘要算法)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-update(input: DataBlob): Promise<void>--><!--Device-Md-update(input: DataBlob): Promise<void>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

<a id="updatesync"></a>
## updateSync

```TypeScript
updateSync(input: DataBlob): void
```

传入消息进行Md更新摘要状态，通过同步方式更新。updateSync和digestSync为两段式接口，需要成组使用。其中digestSync必选，updateSync可选。

> **说明：**  
>  
> Md算法多次调用updateSync更新的代码示例详见开发指导  
> [分段摘要算法](docroot://security/CryptoArchitectureKit/crypto-generate-message-digest.md#分段摘要算法)。

<br><br>**说明：**<br>建议优先使用异步API{@link update}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-updateSync(input: DataBlob): void--><!--Device-Md-updateSync(input: DataBlob): void-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.MessageDigest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 传入的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

## algName

```TypeScript
readonly algName: string
```

代表指定的摘要算法名。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Md-readonly algName: string--><!--Device-Md-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

