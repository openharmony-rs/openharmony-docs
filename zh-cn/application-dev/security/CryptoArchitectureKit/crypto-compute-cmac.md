# 消息认证码计算CMAC(ArkTS)

CMAC通过使用分组密码（如AES）和一个密钥生成认证码，确保消息在传输过程中未被篡改。

## 开发步骤

在调用update接口传入数据时，可以[一次性传入所有数据](#cmac一次性传入数据)，也可以把数据人工分段，然后[分段update](#分段cmac)。对于同一段数据而言，是否分段，计算结果没有差异。对于数据量较大的数据，开发者可以根据实际需求选择是否分段传入。

下面分别提供两种方式的示例代码。

### CMAC（一次性传入数据）

1. 调用[cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac18)，指定消息认证码算法为CMAC，指定对称算法为AES128，生成消息认证码实例（Mac）。

2. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)和[SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1)，生成密钥算法为AES256的对称密钥（SymKey）。
   生成对称密钥的详细开发指导，请参考[指定二进制数据生成对称密钥](crypto-convert-binary-data-to-sym-key.md)。

3. 调用[Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-6)，指定共享对称密钥（SymKey），初始化Mac对象。

4. 调用[Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-8)，传入自定义消息，进行消息认证码计算。单次update的长度没有限制。

5. 调用[Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-2)，获取Mac计算结果。

6. 调用[Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength)，获取Mac长度，单位为字节。

- 以使用await方式一次性传入数据，获取消息认证码计算结果为例：

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey success');
    return symKey;
  }
  async function doCmac() {
    // 把字符串按utf-8解码为Uint8Array，使用固定的128位的密钥，即16字节。
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = await genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let message = 'cmacTestMessage'; // 待进行CMAC的数据。
    let mac = cryptoFramework.createMac(spec);
    await mac.init(key);
    // 数据量不多时，可以一次性更新，将所有数据传入，接口没有入参长度限制。
    await mac.update({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
    let macResult = await mac.doFinal();
    console.info('CMAC result:' + macResult.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```

- 以使用同步方式一次性传入数据，获取消息认证码计算结果为例：

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey =  aesGenerator.convertKeySync(symKeyBlob);
    console.info('[Sync]convertKey success');
    return symKey;
  }
  function doCmacBySync() {
    // 把字符串按utf-8解码为Uint8Array，使用固定的128位的密钥，即16字节。
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let message = 'cmacTestMessage'; // 待进行CMAC的数据。
    let mac = cryptoFramework.createMac(spec);
    mac.initSync(key);
    // 数据量不大时，可以一次性更新，将所有数据传入，接口没有入参长度限制。
    mac.updateSync({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
    let macResult = mac.doFinalSync();
    console.info('[Sync]CMAC result:' + macResult.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```

### 分段CMAC

1. 调用[cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac18)，指定消息认证码算法CMAC，对称算法AES256，生成消息认证码实例（Mac）。

2. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)、[SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1)，生成密钥算法为AES256的对称密钥（SymKey）。
   生成对称密钥的详细开发指导，请参考[指定二进制数据生成对称密钥](crypto-convert-binary-data-to-sym-key.md)。

3. 调用[Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-7)，指定共享对称密钥（SymKey），初始化Mac对象。

4. 传入自定义消息，设置每次传入数据量为20字节，多次调用[Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-9)，计算消息认证码。

5. 调用[Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-3)，获取Mac计算结果。

6. 调用[Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength)，获取Mac消息认证码的长度，单位为字节。

- 以使用await方式分段传入数据，获取消息认证码计算结果为例。

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  async function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = await aesGenerator.convertKey(symKeyBlob);
    console.info('convertKey success');
    return symKey;
  }
  async function doLoopCmac() {
    // 把字符串按utf-8解码为Uint8Array，使用固定的128位的密钥，即16字节。
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = await genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let mac = cryptoFramework.createMac(spec);
    // 假设消息共43字节，根据UTF-8解码后，仍是43字节。
    let messageText = "aaaaa......bbbbb......ccccc......ddddd......eee";
    let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
    let updateLength = 20; // 假设以20字节为单位进行分段update，实际并无具体要求。
    await mac.init(key);
    for (let i = 0; i < messageData.length; i += updateLength) {
      let updateMessage = messageData.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      await mac.update(updateMessageBlob);
    }
    let macOutput = await mac.doFinal();
    console.info("CMAC result: " + macOutput.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```

- 以使用同步方式分段传入数据，获取消息认证码计算结果为例。

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  function genSymKeyByData(symKeyData: Uint8Array) {
    let symKeyBlob: cryptoFramework.DataBlob = { data: symKeyData };
    let aesGenerator = cryptoFramework.createSymKeyGenerator('AES128');
    let symKey = aesGenerator.convertKeySync(symKeyBlob);
    console.info('[Sync]convertKey success');
    return symKey;
  }
  function doLoopCmacBySync() {
    // 把字符串按utf-8解码为Uint8Array，使用固定的128位的密钥，即16字节。
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let mac = cryptoFramework.createMac(spec);
    // 假设信息共43字节，utf-8解码后仍为43字节。
    let messageText = "aaaaa.....bbbbb.....ccccc.....ddddd.....eee";
    let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
    let updateLength = 20; // 假设以20字节为单位进行分段update，实际没有具体要求。
    mac.initSync(key);
    for (let i = 0; i < messageData.length; i += updateLength) {
      let updateMessage = messageData.subarray(i, i + updateLength);
      let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
      mac.updateSync(updateMessageBlob);
    }
    let macOutput = mac.doFinalSync();
    console.info("[Sync]CMAC result: " + macOutput.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```
