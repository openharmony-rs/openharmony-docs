# Random

Random类，调用Random方法生成随机数。调用前，需要通过[createRandom](arkts-cryptoarchitecture-cryptoframework-createrandom-f.md#createrandom-1)构造Random实例。

**起始版本：** 9

<!--Device-cryptoFramework-interface Random--><!--Device-cryptoFramework-interface Random-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="enablehardwareentropy"></a>
## enableHardwareEntropy

```TypeScript
enableHardwareEntropy(): void
```

开启硬件熵源。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Random-enableHardwareEntropy(): void--><!--Device-Random-enableHardwareEntropy(): void-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Rand

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rand = cryptoFramework.createRandom();
rand.enableHardwareEntropy();
rand.generateRandom(12, (err, randData) => {
  if (err) {
    console.error(`[Callback] generate random failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('[Callback]: generate random result: ' + randData.data);
    try {
      rand.setSeed(randData);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

<a id="generaterandom"></a>
## generateRandom

```TypeScript
generateRandom(len: number, callback: AsyncCallback<DataBlob>): void
```

生成指定长度的随机数。使用callback异步回调。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Random-generateRandom(len: int, callback: AsyncCallback<DataBlob>): void--><!--Device-Random-generateRandom(len: int, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| len | number | 是 | 表示生成随机数的长度，单位为bytes，范围在[1, INT_MAX]。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataBlob&gt; | 是 | 回调函数。当生成随机数成功时，err为undefined，data为获取到的随机数；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let rand = cryptoFramework.createRandom();
rand.generateRandom(12, (err, randData) => {
  if (err) {
    console.error(`[Callback] generate random failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('[Callback]: generate random result: ' + randData.data);
  }
});

```

<a id="generaterandom-1"></a>
## generateRandom

```TypeScript
generateRandom(len: number): Promise<DataBlob>
```

生成指定长度的随机数。使用promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Random-generateRandom(len: int): Promise<DataBlob>--><!--Device-Random-generateRandom(len: int): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| len | number | 是 | 表示生成随机数的长度，单位为bytes，范围在[1, INT_MAX]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回生成的随机数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rand = cryptoFramework.createRandom();
let promiseGenerateRand = rand.generateRandom(12);
promiseGenerateRand.then(randData => {
  console.info('[Promise]: rand result: ' + randData.data);
}).catch((error: BusinessError) => {
  console.error(`[Promise] failed: errCode: ${error.code}, errMsg: ${error.message}`);
});

```

JS示例：

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="RandTest">Rand异步测试</input>
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

function randTest() {
    let rand = cryptoFramework.createRandom();
    let seed = new Uint8Array([1, 2, 3]);
    rand.setSeed({ data : seed });

    rand.generateRandom(12, function (finishErr, randData){
        if (finishErr) {
            console.error("GenerateRandom failed. Code:" + finishErr.code + " : " + finishErr.message);
        } else {
            console.info("GenerateRandom successfully:" + randData);
        }
    })
}

export default {
    data: {
        result: ''
    },
    RandTest() {
        randTest();
    }
};

```

<a id="generaterandomsync"></a>
## generateRandomSync

```TypeScript
generateRandomSync(len: number): DataBlob
```

同步生成指定长度的随机数。

<br><br>**说明：**<br>建议优先使用异步API{@link generateRandom}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 10

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本10-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Random-generateRandomSync(len: int): DataBlob--><!--Device-Random-generateRandomSync(len: int): DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| len | number | 是 | 表示生成随机数的长度，单位为bytes，范围在[1, INT_MAX]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 表示生成的随机数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rand = cryptoFramework.createRandom();
try {
  let randData = rand.generateRandomSync(12);
  if (randData != null) {
    console.info('[Sync]: rand result: ' + randData.data);
  } else {
    console.error('[Sync]: get rand result: fail.');
  }
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}

```

JS示例：

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="RandTestSync">Rand同步测试</input>
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

function randTestSync() {
    let rand = cryptoFramework.createRandom();
    let randLen = 24;
    try {
        let randData = rand.generateRandomSync(randLen);
        if (randData != null) {
            console.info("GenerateRandom successfully: " + randData.data);
        } else {
            console.error("GenerateRandom failed!");
        }
    } catch (error) {
        console.error(`GenerateRandom random number failed. Code: ${error.code}, message: ${error.message}`);
    }
}

export default {
    data: {
        result: ''
    },
    RandTestSync() {
        randTestSync();
    }
};

```

<a id="setseed"></a>
## setSeed

```TypeScript
setSeed(seed: DataBlob): void
```

设置指定的种子。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Random-setSeed(seed: DataBlob): void--><!--Device-Random-setSeed(seed: DataBlob): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| seed | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 设置的种子。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rand = cryptoFramework.createRandom();
rand.generateRandom(12, (err, randData) => {
  if (err) {
    console.error(`[Callback] generate random failed, errCode: ${err.code}, errMsg: ${err.message}`);
  } else {
    console.info('[Callback]: generate random result: ' + randData.data);
    try {
      rand.setSeed(randData);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
});

```

## algName

```TypeScript
readonly algName: string
```

代表当前使用的随机数生成算法，目前只支持"CTR_DRBG"。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Random-readonly algName: string--><!--Device-Random-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本10-11：SystemCapability.Security.CryptoFramework

