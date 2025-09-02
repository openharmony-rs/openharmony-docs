# Generating a CMAC

A block cipher (such as AES) and a key are used to generate an authentication code, which verifies that a message has not been alerted during transmission.

## How to Develop

During the CMAC operation, you can [pass in all the data at a time](#generating-a-cmac-by-passing-in-full-data) or [pass in data by segment](#generating-a-cmac-by-passing-in-data-by-segment). The same data will produce the same result no matter how the data is passed. Use the appropriate method based on the data size.

The following provides examples of CMAC operations with different data passing methods.

### Generating a CMAC by Passing in Full Data

1. Call [cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac18) with the MAC algorithm set to **CMAC** and symmetric key algorithm set to **AES256** to create a **Mac** instance.

2. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (**SymKey**) using AES256.
   For details, see [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md).

3. Call [Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-6) to initialize the **Mac** instance using the shared symmetric key (**SymKey**).

4. Call [Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-8) to pass in the full data. The amount of data to be passed in by a single **Mac.update()** call is not limited.

5. Call [Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-2) to generate a MAC.

6. Call [Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength) to obtain the length of the MAC, in bytes.

- Example: Pass in the full data to generate a MAC using **await**.

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
    // Convert the string into a Uint8Array in UTF-8 format and use it as the private key, which is 128 bits (16 bytes).
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = await genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let message = 'cmacTestMessage'; // Message used to generate a CMAC.
    let mac = cryptoFramework.createMac(spec);
    await mac.init(key);
    // For a small amount of data, update it by passing in the full data. The API does not have a limit on the length of input parameters.
    await mac.update({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
    let macResult = await mac.doFinal();
    console.info('CMAC result:' + macResult.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```

- Example: Pass in the full data to calculate a MAC using synchronous APIs.

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
    // Convert the string into a Uint8Array in UTF-8 format and use it as the private key, which is 128 bits (16 bytes).
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let message = 'cmacTestMessage'; // Message used to generate a CMAC.
    let mac = cryptoFramework.createMac(spec);
    mac.initSync(key);
    // For a small amount of data, update it by passing in the full data. The API does not have a limit on the length of input parameters.
    mac.updateSync({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
    let macResult = mac.doFinalSync();
    console.info('[Sync]CMAC result:' + macResult.data);
    let macLen = mac.getMacLength();
    console.info('CMAC len:' + macLen);
  }
  ```

### Generating a CMAC by Passing In Data by Segment

1. Call [cryptoFramework.createMac](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemac18) with the MAC algorithm set to **CMAC** and symmetric key algorithm set to **AES256** to create a **Mac** instance.

2. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) and [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to generate a symmetric key (**SymKey**) using AES256.
   For details, see [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key.md).

3. Call [Mac.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-7) to initialize the **Mac** instance using the shared symmetric key (**SymKey**).

4. Call [Mac.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-9) multiple times to pass in 20 bytes each time.

5. Call [Mac.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-3) to generate a MAC.

6. Call [Mac.getMacLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmaclength) to obtain the length of the MAC, in bytes.

- Example: Pass in data by segment to generate a MAC using **await**.

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
    // Convert the string into a Uint8Array in UTF-8 format and use it as the private key, which is 128 bits (16 bytes).
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = await genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let mac = cryptoFramework.createMac(spec);
    // In this example, the message is of 43 bytes. After decoded in UTF-8 format, the message is also of 43 bytes.
    let messageText = "aaaaa......bbbbb......ccccc......ddddd......eee";
    let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
    let updateLength = 20; // Pass in 20 bytes each time. You can set this parameter as required.
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

- Example: Pass in data by segment to generate a MAC using synchronous APIs.

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
    // Convert the string into a Uint8Array in UTF-8 format and use it as the private key, which is 128 bits (16 bytes).
    let keyData = new Uint8Array(buffer.from("12345678abcdefgh", 'utf-8').buffer);
    let key = genSymKeyByData(keyData);
    let spec: cryptoFramework.CmacSpec = {
        algName: "CMAC",
        cipherName: "AES128",
    };
    let mac = cryptoFramework.createMac(spec);
    // In this example, the message is of 43 bytes. After decoded in UTF-8 format, the message is also of 43 bytes.
    let messageText = "aaaaa.....bbbbb.....ccccc.....ddddd.....eee";
    let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
    let updateLength = 20; // Pass in 20 bytes each time. You can set this parameter as required.
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
