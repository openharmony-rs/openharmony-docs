# 消息认证码计算HMAC(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

HMAC使用指定的摘要算法，以共享密钥和消息作为输入，生成固定长度的消息认证码，用于检验报文的完整性。HMAC在消息摘要算法基础上增加密钥输入，确保信息正确性。

## 开发步骤

在调用update接口传入数据时，可以[一次性传入所有数据](#hmac一次性传入)，也可以把数据人工分段，然后[分段update](#分段hmac)。对于同一段数据而言，是否分段，计算结果没有差异。对于数据量较大的数据，开发者可以根据实际需求选择是否分段传入。

下面分别提供两种方式的示例代码。

### HMAC（一次性传入）

1. 调用[cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac)，指定摘要算法SHA256，生成消息认证码实例（Mac）。

2. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)、[SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1)，生成密钥算法为HMAC的对称密钥（SymKey）。

   详细开发指导请参考[指定二进制数据生成对称密钥](crypto-convert-binary-data-to-sym-key.md)。

3. 调用[Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-6)，指定共享对称密钥（SymKey），初始化Mac对象。

4. 调用[Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-8)，传入自定义消息，进行消息认证码计算。单次update长度没有限制。

5. 调用[Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-2)，获取Mac计算结果。

6. 调用[Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength)，获取Mac消息认证码的长度，单位为字节。

- 以使用await方式一次性传入数据，获取消息认证码计算结果为例：
<!-- @[message_authentication_code_calculated_as_fragmented_hmac_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/ets/pages/HMACSingleTime/Async.ets) -->


- 以使用同步方式一次性传入数据，获取消息认证码计算结果为例：

<!-- @[message_authentication_code_calculated_as_fragmented_hmac_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/ets/pages/HMACSingleTime/Sync.ets) -->


### 分段HMAC

1. 调用[cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac)，指定摘要算法SHA256，生成消息认证码实例（Mac）。

2. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)和[SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1)，生成密钥算法为HMAC的对称密钥（SymKey）。

   生成对称密钥的开发指导，请参考[指定二进制数据生成对称密钥](crypto-convert-binary-data-to-sym-key.md)。

3. 调用[Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-7)，指定共享对称密钥（SymKey），初始化Mac对象。

4. 传入自定义消息，将一次传入数据量设置为20字节，多次调用[Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-9)，进行消息认证码计算。

5. 调用[Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-3)，获取Mac计算结果。

6. 调用[Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength)，获取Mac消息认证码的长度，单位为字节。

- 使用await方式分段传入数据，获取消息认证码计算结果。

<!-- @[message_authentication_code_calculation_hmac_one_time_incoming](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/ets/pages/HMACSegmentation/Async.ets) -->


- 使用同步方式分段传入数据，获取消息认证码计算结果。

<!-- @[message_authentication_code_calculation_sync_one_time_incoming](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/ets/pages/HMACSegmentation/Sync.ets) -->



### HMAC(HmacSpec作为参数传入)
1. 调用[cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac)，指定消息认证码算法HMAC，指定摘要算法SHA256，生成消息认证码实例（Mac）。

2. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)和[SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1)，生成密钥算法为HMAC的对称密钥（SymKey）。

   参考[指定二进制数据生成对称密钥](crypto-convert-binary-data-to-sym-key.md)。

3. 调用[Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-6)，指定共享对称密钥（SymKey），初始化Mac对象。

4. 调用[Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-8)，传入自定义消息，进行消息认证码计算。单次update长度没有限制。

5. 调用[Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-2)，获取Mac计算结果。

6. 调用[Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength)，获取Mac消息认证码的长度，单位为字节。

- 以使用await方式一次性传入数据，获取消息认证码计算结果为例：

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey success');
    return symKey;
  }
  async function doHmac() {
    // 把字符串按utf-8解码为Uint8Array，使用固定的128位的密钥，即16字节。
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = await genSymKeyByData(keyData);
    let spec: cryptoFramework.HmacSpec = {
        algName: "HMAC",
        mdName: "SHA256",
    };
    let message = 'hmacTestMessage'; // 待进行HMAC的数据。
    let mac = cryptoFramework.createMac(spec);
    await mac.init(key);
    // 数据量较少时，可以只做一次update，将所有数据传入，接口不对参数长度设限。
    await mac.update({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
    let macResult = await mac.doFinal();
    console.info('HMAC result:' + macResult.data);
    let macLen = mac.getMacLength();
    console.info('HMAC len:' + macLen);
  }
  ```