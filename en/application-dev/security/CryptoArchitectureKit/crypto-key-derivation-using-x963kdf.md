# Key Derivation Using X963KDF (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

From API version 22, the crypto algorithm library supports key derivation with X963KDF.

For details about the corresponding algorithm specifications, see [X963KDF](crypto-key-derivation-overview.md#x963kdf).

## How to Develop

1. Create an [X963KdfSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#x963kdfspec22) object and use it as a parameter for key derivation.

   **X963KdfSpec** is a child class of [KdfSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#kdfspec11). You need to specify the following:

   - **algName**: algorithm to used, which is **'X963Kdf'**.
   - **key**: original key material.
      If the string type is used, pass in the data used for key derivation instead of the string type such as HexString or base64. In addition, ensure that the string is encoded in UTF-8 format. Otherwise, the derived key may be different from what you expected.
   - **info**: optional context and application information used to extend the short key. This parameter can be empty.
   - **keySize**: length of the key to derive, in bytes. The value must be a positive integer.

2. Call [cryptoFramework.createKdf](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekdf11) with the string parameter **'X963KDF|SHA256'** to create a **Kdf** object. The key derivation algorithm is **X963KDF**, and HMAC algorithm is **SHA256**.

3. Call [Kdf.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11) with the **X963KdfSpec** object to generate a derived key.

   The following table lists how **Kdf.generateSecret** delivers the return value.

   | Name| Return Mode|
   | -------- | -------- |
   | generateSecret(params: KdfSpec, callback: AsyncCallback&lt;DataBlob&gt;): void | This API uses an asynchronous callback to return the result.|
   | generateSecret(params: KdfSpec): Promise&lt;DataBlob&gt; | This API uses a promise to return the result.|
   | generateSecretSync(params: KdfSpec): DataBlob | This API returns the result synchronously.|

- Return the result using **await**:

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';

  async function kdfAwait() {
    let keyData = new Uint8Array(buffer.from("012345678901234567890123456789", "utf-8").buffer);
    let infoData = new Uint8Array(buffer.from("infostring", "utf-8").buffer);
    let spec: cryptoFramework.X963KdfSpec = {
      algName: 'X963KDF',
      key: keyData,
      info: infoData,
      keySize: 32
    };
    let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
    let secret = await kdf.generateSecret(spec);
    console.info("key derivation output is " + secret.data);
  }
  ```

- Return the result using a promise:

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  function kdfPromise() {
    let keyData = new Uint8Array(buffer.from("012345678901234567890123456789", "utf-8").buffer);
    let infoData = new Uint8Array(buffer.from("infostring", "utf-8").buffer);
    let spec: cryptoFramework.X963KdfSpec = {
      algName: 'X963KDF',
      key: keyData,
      info: infoData,
      keySize: 32
    };
    let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
    let kdfPromise = kdf.generateSecret(spec);
    kdfPromise.then((secret) => {
      console.info("key derivation output is " + secret.data);
    }).catch((error: BusinessError) => {
      console.error("key derivation error.");
    });
  }
  ```

- Return the result synchronously:

  ```ts
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  function kdfSync() {
    let keyData = new Uint8Array(buffer.from("012345678901234567890123456789", "utf-8").buffer);
    let infoData = new Uint8Array(buffer.from("infostring", "utf-8").buffer);
    let spec: cryptoFramework.X963KdfSpec = {
      algName: 'X963KDF',
      key: keyData,
      info: infoData,
      keySize: 32
    };
    let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
    let secret = kdf.generateSecretSync(spec);
    console.info("[Sync]key derivation output is " + secret.data);
  }
  ```
