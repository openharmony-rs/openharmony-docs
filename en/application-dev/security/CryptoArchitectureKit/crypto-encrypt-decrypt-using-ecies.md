# Encryption and Decryption Using ECIES (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The ECIES algorithm is supported since API version 26.0.0. It is an encryption algorithm based on elliptic curve cryptography.

**Constraints**

- Key agreement algorithms ECC256, ECC384, and ECC521 are supported.
- Among key derivation algorithms, only X963KDF is supported. Digest algorithms SHA-1, SHA-256, SHA-384, and SHA-512 are supported.
- Symmetric encryption algorithms AES-128, AES-192, and AES-256 are supported.
- Among block cipher modes, only GCM is supported.

## Development Procedure

### Encryption

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [SymKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair) to generate a key pair using the ECC algorithm.

2. Call [cryptoFramework.createKeyAgreement](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekeyagreement) and [KeyAgreement.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11) to perform key agreement based on the local private key (KeyPair.priKey) and peer public key (KeyPair.pubKey) and return the shared key.

3. Call [cryptoFramework.createKdf](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekdf11) and [Kdf.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11) to derive a key based on the shared key (Secret) using the X963KDF algorithm and return the derived key.

4. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'AES128|GCM'** to create a **Cipher** instance for encryption. The key type is AES-128, and the block cipher mode is GCM.

5. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.ENCRYPT_MODE** (encryption), key to **SymKey** (the key for encryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

6. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass the data to be encrypted (plaintext).

7. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the encrypted data.

8. Obtain [GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag as the authentication information for decryption.

### Decryption

1. Call [cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator) and [SymKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair) to generate a key pair using the ECC algorithm.

2. Call [cryptoFramework.createKeyAgreement](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekeyagreement) and [KeyAgreement.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11) to perform key agreement based on the local private key (KeyPair.priKey) and peer public key (KeyPair.pubKey) and return the shared key.

3. Call [cryptoFramework.createKdf](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatekdf11) and [Kdf.generateSecret](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesecret11) to derive a key based on the shared key (Secret) using the X963KDF algorithm and return the derived key.

4. Call [cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher) with the string parameter **'AES128|GCM'** to create a **Cipher** instance for decryption. The key type is AES-128, and the block cipher mode is GCM.

5. Call [Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1) to initialize the **Cipher** instance. Specifically, set the mode to **cryptoFramework.CryptoMode.DECRYPT_MODE** (decryption), key to **SymKey** (the key for decryption), and parameter to **GcmParamsSpec** corresponding to the GCM mode.

6. Call [Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1) to pass the data to be decrypted (ciphertext).

7. Call [Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1) to obtain the decrypted data.

### Example Code

- Example (using asynchronous APIs):

  <!-- @[use_sample_await_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/ets/pages/Await.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  namespace ECIES {
    function generateGcmParamsSpec(ivData: Uint8Array): cryptoFramework.GcmParamsSpec {
      let ivBlob: cryptoFramework.DataBlob = {
        data: ivData,
      };
      let rand: cryptoFramework.Random = cryptoFramework.createRandom();
      let aadBlob: cryptoFramework.DataBlob = rand.generateRandomSync(8);
      let tagBlob: cryptoFramework.DataBlob = rand.generateRandomSync(16);
      // Obtain the GCM authTag from the Cipher.doFinal result in encryption and fill it in the params parameter of Cipher.init in decryption.
      let gcmParams: cryptoFramework.GcmParamsSpec = {
        iv: ivBlob,
        aad: aadBlob,
        authTag: tagBlob,
        algName: 'GcmParamsSpec',
      };
      return gcmParams;
    }
  
    async function generateSecret(priKey: cryptoFramework.PriKey, pubKey: cryptoFramework.PubKey):
      Promise<cryptoFramework.DataBlob> {
      // EC key agreement.
      let agreement: cryptoFramework.KeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
      let keyData: cryptoFramework.DataBlob = await agreement.generateSecret(priKey, pubKey);
  
      let infoData: Uint8Array = new Uint8Array(buffer.from('infostring', 'utf-8').buffer);
      let spec: cryptoFramework.X963KdfSpec = {
        algName: 'X963KDF',
        key: keyData.data,
        info: infoData,
        keySize: 32, // The first 16 bytes are used as the IV of AES-128, and the last 16 bytes are used as the key.
      };
  
      // Derive the key using X963KDF.
      let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
      let secret = await kdf.generateSecret(spec);
      return secret;
    }
  
    async function generateSymKey(secret: cryptoFramework.DataBlob): Promise<cryptoFramework.SymKey> {
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
      let keyData: cryptoFramework.DataBlob = {
        data: secret.data.slice(16),
      };
      let symKey: cryptoFramework.SymKey = await symKeyGenerator.convertKey(keyData);
      return symKey;
    }
  
    async function encrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      plainText: cryptoFramework.DataBlob): Promise<cryptoFramework.DataBlob> {
      // AES-GCM symmetric encryption
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      await cipher.init(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
      let cipherText: cryptoFramework.DataBlob = await cipher.update(plainText);
      gcmParams.authTag = await cipher.doFinal(null);
      return cipherText;
    }
  
    async function decrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      cipherText: cryptoFramework.DataBlob): Promise<cryptoFramework.DataBlob> {
      // AES-GCM symmetric decryption.
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      await cipher.init(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
      let plainText: cryptoFramework.DataBlob = await cipher.doFinal(cipherText);
      return plainText;
    }
  
    export async function doEciesTest(): Promise<string> {
      try {
        // Generate EC key pairs for ends A and B.
        let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
        let keyPairA: cryptoFramework.KeyPair = asyKeyGenerator.generateKeyPairSync();
        let keyPairB: cryptoFramework.KeyPair = asyKeyGenerator.generateKeyPairSync();
  
        // Encryption at end A: private key of end A + public key of end B
        let secretA: cryptoFramework.DataBlob = await generateSecret(keyPairA.priKey, keyPairB.pubKey);
        let symKeyA: cryptoFramework.SymKey = await generateSymKey(secretA);
        let ivData: Uint8Array = secretA.data.slice(0, 16);
        let gcmParams: cryptoFramework.GcmParamsSpec = generateGcmParamsSpec(ivData);
  
        let message: string = 'This is a test message!!!';
        let plainText: cryptoFramework.DataBlob = {
          data: new Uint8Array(buffer.from(message, 'utf-8').buffer),
        };
        let cipherData: cryptoFramework.DataBlob = await encrypt(symKeyA, gcmParams, plainText);
  
        // Decryption at end B: private key of end B + public key of end A
        let secretB: cryptoFramework.DataBlob = await generateSecret(keyPairB.priKey, keyPairA.pubKey);
        let symKeyB: cryptoFramework.SymKey = await generateSymKey(secretB);
        let plainData: cryptoFramework.DataBlob = await decrypt(symKeyB, gcmParams, cipherData);
        console.info('doEciesTest success, message: ' + buffer.from(plainData.data).toString('utf-8'));
        return 'Success';
      } catch (error) {
        console.error(`doEciesTest failed, error: + ${JSON.stringify(error)}`);
        return 'Failed';
      }
    }
  }
  ```

- Example (using synchronous APIs):

  <!-- @[use_sample_sync_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/ets/pages/Sync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { buffer } from '@kit.ArkTS';
  
  namespace ECIES {
    function generateGcmParamsSpec(ivData: Uint8Array): cryptoFramework.GcmParamsSpec {
      let ivBlob: cryptoFramework.DataBlob = {
        data: ivData,
      };
      let rand: cryptoFramework.Random = cryptoFramework.createRandom();
      let aadBlob: cryptoFramework.DataBlob = rand.generateRandomSync(8);
      let tagBlob: cryptoFramework.DataBlob = rand.generateRandomSync(16);
      // Obtain the GCM authTag from the Cipher.doFinal result in encryption and fill it in the params parameter of Cipher.init in decryption.
      let gcmParams: cryptoFramework.GcmParamsSpec = {
        iv: ivBlob,
        aad: aadBlob,
        authTag: tagBlob,
        algName: 'GcmParamsSpec',
      };
      return gcmParams;
    }
  
    function generateSecret(priKey: cryptoFramework.PriKey, pubKey: cryptoFramework.PubKey):
      cryptoFramework.DataBlob {
      // EC key agreement.
      let agreement: cryptoFramework.KeyAgreement = cryptoFramework.createKeyAgreement('ECC256');
      let keyData: cryptoFramework.DataBlob = agreement.generateSecretSync(priKey, pubKey);
  
      let infoData: Uint8Array = new Uint8Array(buffer.from('infostring', 'utf-8').buffer);
      let spec: cryptoFramework.X963KdfSpec = {
        algName: 'X963KDF',
        key: keyData.data,
        info: infoData,
        keySize: 32, // The first 16 bytes are used as the IV of AES-128, and the last 16 bytes are used as the key.
      };
  
      // Derive the key using X963KDF.
      let kdf = cryptoFramework.createKdf('X963KDF|SHA256');
      let secret = kdf.generateSecretSync(spec);
      return secret;
    }
  
    function generateSymKey(secret: cryptoFramework.DataBlob): cryptoFramework.SymKey {
      let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
      let keyData: cryptoFramework.DataBlob = {
        data: secret.data.slice(16),
      };
      let symKey: cryptoFramework.SymKey = symKeyGenerator.convertKeySync(keyData);
      return symKey;
    }
  
    function encrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      plainText: cryptoFramework.DataBlob): cryptoFramework.DataBlob {
      // AES-GCM symmetric encryption
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      cipher.initSync(cryptoFramework.CryptoMode.ENCRYPT_MODE, symKey, gcmParams);
      let cipherText: cryptoFramework.DataBlob = cipher.updateSync(plainText);
      gcmParams.authTag = cipher.doFinalSync(null);
      return cipherText;
    }
  
    function decrypt(symKey: cryptoFramework.SymKey, gcmParams: cryptoFramework.GcmParamsSpec,
      cipherText: cryptoFramework.DataBlob): cryptoFramework.DataBlob {
      // AES-GCM symmetric decryption.
      let cipher: cryptoFramework.Cipher = cryptoFramework.createCipher('AES128|GCM');
      cipher.initSync(cryptoFramework.CryptoMode.DECRYPT_MODE, symKey, gcmParams);
      let plainText: cryptoFramework.DataBlob = cipher.doFinalSync(cipherText);
      return plainText;
    }
  
    export function doEciesTest(): string {
      try {
        // Generate EC key pairs for ends A and B.
        let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
        let keyPairA: cryptoFramework.KeyPair = asyKeyGenerator.generateKeyPairSync();
        let keyPairB: cryptoFramework.KeyPair = asyKeyGenerator.generateKeyPairSync();
  
        // Encryption at end A: private key of end A + public key of end B
        let secretA: cryptoFramework.DataBlob = generateSecret(keyPairA.priKey, keyPairB.pubKey);
        let symKeyA: cryptoFramework.SymKey = generateSymKey(secretA);
        let ivData: Uint8Array = secretA.data.slice(0, 16);
        let gcmParams: cryptoFramework.GcmParamsSpec = generateGcmParamsSpec(ivData);
  
        let message: string = 'This is a test message!!!';
        let plainText: cryptoFramework.DataBlob = {
          data: new Uint8Array(buffer.from(message, 'utf-8').buffer),
        };
        let cipherData: cryptoFramework.DataBlob = encrypt(symKeyA, gcmParams, plainText);
  
        // Decryption at end B: private key of end B + public key of end A
        let secretB: cryptoFramework.DataBlob = generateSecret(keyPairB.priKey, keyPairA.pubKey);
        let symKeyB: cryptoFramework.SymKey = generateSymKey(secretB);
        let plainData: cryptoFramework.DataBlob = decrypt(symKeyB, gcmParams, cipherData);
        console.info('doEciesTest success, message: ' + buffer.from(plainData.data).toString('utf-8'));
        return 'Success';
      } catch (error) {
        console.error(`doEciesTest failed, error: + ${JSON.stringify(error)}`);
        return 'Failed';
      }
    }
  }
  ```
