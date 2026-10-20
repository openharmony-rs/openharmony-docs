# Mac

```TypeScript
interface Mac
```

消息认证码接口，定义基于对称密钥计算消息认证码的方法。调用前，需通过[createMac](arkts-cryptoarchitecture-cryptoframework-createmac-f.md#createmac)方法创建一个Mac实例。

**起始版本：** 9

<!--Device-cryptoFramework-interface Mac--><!--Device-cryptoFramework-interface Mac-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## doFinal

```TypeScript
doFinal(callback: AsyncCallback<DataBlob>): void
```

完成MAC计算并获取MAC计算结果。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-doFinal(callback: AsyncCallback<DataBlob>): void--><!--Device-Mac-doFinal(callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | 是 | 回调函数。当MAC计算成功时，err为undefined，data为获取到的Mac计算结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

此外，更多HMAC的完整示例可参考开发指导中[消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function hmacByCallback() {
  let mac = cryptoFramework.createMac('SHA256');
  let keyBlob: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('12345678abcdefgh', 'utf-8').buffer) };
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  symKeyGenerator.convertKey(keyBlob, (err, symKey) => {
    mac.init(symKey, (err) => {
      mac.update({ data: new Uint8Array(buffer.from('hmacTestMessage', 'utf-8').buffer) }, (err) => {
        mac.doFinal((err, output) => {
          console.info('[Callback]: HMAC result: ' + output.data);
          console.info('[Callback]: MAC len: ' + mac.getMacLength());
        });
      });
    });
  });
}
```

JS示例：

在Lite Wearable侧HMAC消息认证码支持的摘要算法只有SHA256。

下述样例以摘要算法为SHA256，对称算法为HMAC为例。

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="HmacTest">Hmac异步测试</input>
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
 
let plainText = "hmacTestMessage";
 
function hmacTest() {
  try {
      let hmacSpec = { algName: 'HMAC', mdName: 'SHA256' };
      let keyData = StringToUint8Array("12345678abcdefgh");
      let mac = cryptoFramework.createMac(hmacSpec);
      console.info('createMac ' + typeof mac);
  
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
      symKeyGenerator.convertKey({ data: keyData }, function (err, symKey) {
          if (err) {
              console.error('convertKey failed. Code: ' + err.code + " : " + err.message);
              return;
          }
          mac.init(symKey, function (err) {
              if (err) {
                  console.error('Mac init failed. Code: ' + err.code + " : " + err.message);
                  return;
              }
              mac.update({ data: StringToUint8Array(plainText) }, function (err) {
                  if (err) {
                      console.error('Mac update failed. Code: ' + err.code + " : " + err.message);
                      return;
                  }
                  mac.doFinal(function (err, output) {
                      if (err) {
                          console.error('Mac doFinal failed. Code: ' + err.code + " : " + err.message);
                      } else {
                          console.info('Mac doFinal successfully: ' + output.data);
                          console.info('Mac len: ' + mac.getMacLength());
                      }
                  })
              })
          })
      })
    } catch (error) {
        console.error(`hmacTest failed. Code: ${error.code}, message: ${error.message}`);
  }
}
 
export default {
    data: {
        result: ''
    },
    HmacTest() {
        hmacTest();
    }
};
```

## doFinal

```TypeScript
doFinal(): Promise<DataBlob>
```

完成MAC计算并获取MAC计算结果。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-doFinal(): Promise<DataBlob>--><!--Device-Mac-doFinal(): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise对象，返回MAC计算结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 26.2.0+ |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

此外，更多HMAC的完整示例可参考开发指导[消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

async function hmacByPromise() {
  let mac = cryptoFramework.createMac('SHA256');
  let keyBlob: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('12345678abcdefgh', 'utf-8').buffer) };
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let symKey = await symKeyGenerator.convertKey(keyBlob);
  await mac.init(symKey);
  await mac.update({ data: new Uint8Array(buffer.from('hmacTestMessage', 'utf-8').buffer) });
  let macOutput = await mac.doFinal();
  console.info('[Promise]: HMAC result: ' + macOutput.data);
  console.info('[Promise]: MAC len: ' + mac.getMacLength());
}
```

## doFinalSync

```TypeScript
doFinalSync(): DataBlob
```

通过同步方式完成MAC计算并获取MAC计算结果。

<br><br>**说明：** <br>建议优先使用异步API，doFinal。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-doFinalSync(): DataBlob--><!--Device-Mac-doFinalSync(): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 返回MAC计算结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

此外，更多HMAC的完整示例可参考开发指导[消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

ArkTS示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function hmacBySync() {
  let mac = cryptoFramework.createMac('SHA256');
  let keyBlob: cryptoFramework.DataBlob = { data: new Uint8Array(buffer.from('12345678abcdefgh', 'utf-8').buffer) };
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let symKey = symKeyGenerator.convertKeySync(keyBlob);
  mac.initSync(symKey);
  mac.updateSync({ data: new Uint8Array(buffer.from('hmacTestMessage', 'utf-8').buffer) });
  let macOutput = mac.doFinalSync();
  console.info('[Sync]: HMAC result: ' + macOutput.data);
  console.info('[Sync]: MAC len: ' + mac.getMacLength());
}
```

JS示例：

在Lite Wearable侧HMAC消息认证码支持的摘要算法只有SHA256。

下述样例以摘要算法为SHA256，对称算法为HMAC为例。

```TypeScript
<div class="container">
    <text class="TestTitle">Crypto测试</text>
    <input class="btn" @click="HmacTestSync">Hmac同步测试</input>
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
 
function hmacTestSync() {
  try {
      let hmacSpec = { algName: 'HMAC', mdName: 'SHA256' };
      let keyData = StringToUint8Array("12345678abcdefgh");
      let message = "hmacTestMessage";
      let mac = cryptoFramework.createMac(hmacSpec);
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
      let symKey = symKeyGenerator.convertKeySync({ data: keyData });
      mac.initSync(symKey);
      mac.updateSync({ data: StringToUint8Array(message) });
      let macOutput = mac.doFinalSync();
      console.info('Mac doFinal successfully: ' + macOutput.data);
  } catch (error) {
      console.error(`GenerateRandom random number failed. Code: ${error.code}, message: ${error.message}`);
  }
}
 
export default {
    data: {
        result: ''
    },
    HmacTestSync() {
        hmacTestSync();
    }
};
```

## getMacLength

```TypeScript
getMacLength(): number
```

获取Mac消息认证码的长度（字节数）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-getMacLength(): int--><!--Device-Mac-getMacLength(): int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回Mac计算结果的字节长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 26.2.0+ |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function testGetMacLength() {
  let mac = cryptoFramework.createMac('SHA256');
  console.info('Mac algName is: ' + mac.algName);
  let keyData = new Uint8Array([83, 217, 231, 76, 28, 113, 23, 219, 250, 71, 209, 210, 205, 97, 32, 159]);
  let keyBlob: cryptoFramework.DataBlob = { data: keyData };
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  let promiseConvertKey = symKeyGenerator.convertKey(keyBlob);
  promiseConvertKey.then(symKey => {
    let promiseMacInit = mac.init(symKey);
    return promiseMacInit;
  })
    .then(() => {
      let blob: cryptoFramework.DataBlob = { data: new Uint8Array([83]) };
      let promiseMacUpdate = mac.update(blob);
      return promiseMacUpdate;
    })
    .then(() => {
      let promiseMacDoFinal = mac.doFinal();
      return promiseMacDoFinal;
    })
    .then(macOutput => {
      console.info('[Promise]: HMAC result: ' + macOutput.data);
      let macLen = mac.getMacLength();
      console.info('MAC len: ' + macLen);
    })
    .catch((error: BusinessError) => {
      console.error(`[Promise] failed: errCode: ${error.code}, errMsg: ${error.message}`);
    });
}
```

## init

```TypeScript
init(key: SymKey, callback: AsyncCallback<void>): void
```

使用对称密钥初始化Mac计算。使用callback异步回调。init、update、doFinal为三段式接口，需要成组使用。其中init和doFinal必选，update可选。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-init(key: SymKey, callback: AsyncCallback<void>): void--><!--Device-Mac-init(key: SymKey, callback: AsyncCallback<void>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 是 | 对称密钥。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当HMAC初始化成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync/Async] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## init

```TypeScript
init(key: SymKey): Promise<void>
```

使用对称密钥初始化Mac计算。使用Promise异步回调。init、update、doFinal为三段式接口，需要成组使用。其中init和doFinal必选，update可选。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-init(key: SymKey): Promise<void>--><!--Device-Mac-init(key: SymKey): Promise<void>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 是 | 对称密钥。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync/Async] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 26.2.0+ |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## initSync

```TypeScript
initSync(key: SymKey): void
```

使用对称密钥初始化Mac计算，通过同步方式获取结果。initSync、updateSync、doFinalSync为三段式接口，需要成组使用。其中initSync和doFinalSync必选，updateSync可选。

<br><br>**说明：** <br>建议优先使用异步API，init。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-initSync(key: SymKey): void--><!--Device-Mac-initSync(key: SymKey): void-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 是 | 对称密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## update

```TypeScript
update(input: DataBlob, callback: AsyncCallback<void>): void
```

传入消息进行Mac更新消息认证码状态。使用callback异步回调。

> **说明：** 
> 
> HMAC算法多次调用update更新的代码示例详见[消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-update(input: DataBlob, callback: AsyncCallback<void>): void--><!--Device-Mac-update(input: DataBlob, callback: AsyncCallback<void>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当HMAC更新成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync/Async] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## update

```TypeScript
update(input: DataBlob): Promise<void>
```

传入消息进行Mac更新消息认证码状态。使用Promise异步回调。

> **说明：** 
> 
> HMAC算法多次调用update更新的代码示例详见[消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-update(input: DataBlob): Promise<void>--><!--Device-Mac-update(input: DataBlob): Promise<void>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync/Async] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported.<br>**适用版本：** 26.2.0+ |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## updateSync

```TypeScript
updateSync(input: DataBlob): void
```

传入消息进行Mac更新消息认证码状态，通过同步方式获取结果。

> **说明：** 
> 
> HMAC算法多次调用updateSync更新的代码示例详见
> [消息认证码计算](../../../security/CryptoArchitectureKit/crypto-compute-hmac.md#分段hmac)。

<br><br>**说明：** <br>建议优先使用异步API，update。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-updateSync(input: DataBlob): void--><!--Device-Mac-updateSync(input: DataBlob): void-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Mac

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync] Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

## algName

```TypeScript
readonly algName: string
```

代表指定的摘要算法名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Mac-readonly algName: string--><!--Device-Mac-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Mac
- API版本9-11：SystemCapability.Security.CryptoFramework
