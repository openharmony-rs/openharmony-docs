# Converting Binary Data into a Symmetric Key (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

This topic uses 3DES and HMAC as an example to describe how to convert binary data into a symmetric key (**SymKey**). That is, convert a piece of external or internal binary data into a key object for subsequent operations, such as encryption and decryption.

## Converting Binary Data into a 3DES Key

For details about the algorithm specifications, see [3DES](crypto-sym-key-generation-conversion-spec.md#3des).

1. Obtain the 3DES binary key data and encapsulate it into a [DataBlob](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#datablob) object.

2. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) with the string parameter **'3DES192'** to create a symmetric key generator (**SymKeyGenerator**) object for a 192-bit 3DES key.

3. Call [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to convert the binary data into a symmetric key (**SymKey**).

4. Call [SymKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the key.

- Example: Convert binary data into a 192-bit 3DES key (using callback-based APIs).

  <!-- @[generate_3des_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormatArkTS/entry/src/main/ets/pages/3des/Callback.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function genKeyMaterialBlob(): cryptoFramework.DataBlob {
    let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
      0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
      0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // The key length is 192 bits, that is, 24 bytes.
    let keyMaterial = new Uint8Array(arr);
    return { data: keyMaterial };
  }
  
  function testConvertSymKey() {
    // Create a SymKeyGenerator instance.
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    // Convert the data into a symmetric key.
    let keyMaterialBlob = genKeyMaterialBlob();
    try {
      symKeyGenerator.convertKey(keyMaterialBlob, (error, key) => {
        if (error) {// If the service logic fails to be executed, the first parameter of the callback returns error information, that is, throw an exception asynchronously.
          let e: BusinessError = error as BusinessError;
          console.error(`convertKey failed: errCode: ${e.code}, message: ${e.message}`);
          return;
        }
        console.info('key algName: '+ key.algName);
        console.info('key format: ' + key.format);
        let encodedKey = key.getEncoded(); // Obtain the binary data of the symmetric key and output the data as a byte array. The length is 24 bytes.
        console.info('key getEncoded hex: ' + encodedKey.data);
      })
    } catch (error) {// Throw an exception immediately when an error is detected during parameter check.
      let e: BusinessError = error as BusinessError;
      console.error(`convertKey failed: errCode: ${e.code}, message: ${e.message}`);
    }
  }
  ```


- Example using synchronous API [convertKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkeysync12):

  <!-- @[generate_3des_key_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormatArkTS/entry/src/main/ets/pages/3des/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  function genKeyMaterialBlob(): cryptoFramework.DataBlob {
    let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
      0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
      0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // The key length is 192 bits, that is, 24 bytes.
    let keyMaterial = new Uint8Array(arr);
    return { data: keyMaterial };
  }
  
  function testConvertSymKey() {
    // Create a SymKeyGenerator instance.
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
    // Convert the data into a symmetric key.
    let keyMaterialBlob = genKeyMaterialBlob();
    try {
      symKeyGenerator.convertKey(keyMaterialBlob, (error, key) => {
        if (error) {// If the service logic fails to be executed, the first parameter of the callback returns error information, that is, throw an exception asynchronously.
          let e: BusinessError = error as BusinessError;
          console.error(`convertKey failed: errCode: ${e.code}, message: ${e.message}`);
          return;
        }
        console.info('key algName: '+ key.algName);
        console.info('key format: ' + key.format);
        let encodedKey = key.getEncoded () // Obtain the binary data of the symmetric key and output the data as a byte array. The length is 24 bytes.
        console.info('key getEncoded hex: ' + encodedKey.data);
      })
    } catch (error) {// Throw an exception immediately when an error is detected during parameter check.
      let e: BusinessError = error as BusinessError;
      console.error(`convertKey failed: errCode: ${e.code}, message: ${e.message}`);
    }
  }
  ```


## Converting Binary Data into an HMAC Key

For details, see [HMAC](crypto-sym-key-generation-conversion-spec.md#hmac).

1. Obtain the HMAC binary key data and encapsulate it into a [DataBlob](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#datablob) object.

2. Call [cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator) with the string parameter **'HMAC'** to create a symmetric key generator (**SymKeyGenerator**) object for an HMAC key of [1, 32768] bits.

3. Call [SymKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-1) to convert the binary data into a symmetric key (**SymKey**).

4. Call [SymKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded) to obtain the binary data of the key.

- Example using **await** to generate a HMAC key:

  <!-- @[generate_hmac_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormatArkTS/entry/src/main/ets/pages/hmac/Await.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  async function testConvertHmacKey() {
    // The symmetric key length is 64 bytes, that is, 512 bits.
    let keyMessage = '12345678abcdefgh12345678abcdefgh12345678abcdefgh12345678abcdefgh';
    let keyBlob: cryptoFramework.DataBlob = {
      data: new Uint8Array(buffer.from(keyMessage, 'utf-8').buffer)
    }
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
    let key = await symKeyGenerator.convertKey(keyBlob);
    let encodedKey = key.getEncoded();
    console.info('key encoded data: ' + encodedKey.data);
  }
  ```


- Example using synchronous API [convertKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkeysync12):

  <!-- @[generate_hmac_key_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ConvertSymmetricKeyBinaryFormatArkTS/entry/src/main/ets/pages/hmac/Sync.ets) -->

  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';

  function testConvertKeySync() {
    // The symmetric key length is 64 bytes, that is, 512 bits.
    let keyMessage = '12345678abcdefgh12345678abcdefgh12345678abcdefgh12345678abcdefgh';
    let keyBlob: cryptoFramework.DataBlob = {
      data : new Uint8Array(buffer.from(keyMessage, 'utf-8').buffer)
    }
    let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
    let key = symKeyGenerator.convertKeySync(keyBlob);
    let encodedKey = key.getEncoded();
    console.info('key encoded data: ' + encodedKey.data);
  }
  ```
