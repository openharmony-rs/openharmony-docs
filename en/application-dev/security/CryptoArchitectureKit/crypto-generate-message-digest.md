# Generating an MD Using SHA-256 (ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ae6edf9e57a4f160cca98ef88ced0cd8e0518bb0 translatedAt=2026-11-04T08:19:27.144Z pushedAt=2026-11-04T08:24:39.627Z nl=1 -->

For details about the algorithm specifications, see [Supported Algorithms and Specifications](crypto-generate-message-digest-overview.md#supported-algorithms-and-specifications).

> **NOTE**
> 
> Starting from API version 12, lightweight smart wearable devices support message digest computation and operations.

## How to Develop

During the MD operation, you can [pass in all the data at a time](#generating-an-md-by-passing-in-full-data) or [pass in data by segment](#generating-an-md-by-passing-in-data-by-segment). For the same piece of data, the result will be the same no matter how the data is passed. Use the appropriate method based on the data size.

The following provides examples of MD operations with different data passing methods.

### Generating an MD by Passing In Full Data

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) with the MD algorithm **SHA256** to create a message digest (**Md**) instance.

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6) to pass in the full data. The data to be passed in by a single **update()** operation is not size bound.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest) to generate an MD.

4. Call [Md.getMdLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmdlength) to obtain the MD length, in bytes.

- Example: Pass in the full data to generate an MD using **await**.

  <!-- @[message_digest_sha256_single_time_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/sha256/singleTime/SingleTimeAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  
  async function doMd() {
    try {
      let mdAlgName = 'SHA256'; // Digest algorithm name.
      let message = 'mdTestMessage'; // Data to be digested.
      let md = cryptoFramework.createMd(mdAlgName);
      // When the amount of data is small, you can call update only once to pass in all the data at once. The API does not limit the length of the input parameter.
      await md.update({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
      let mdResult = await md.digest();
      console.info('Md result: ' + mdResult.data);
      let mdLen = md.getMdLength();
      console.info('md len: ' + mdLen);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```


- Example: Pass in the full data to generate an MD using a synchronous API.

  <!-- @[message_digest_sha256_single_time_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/sha256/singleTime/SingleTimeSync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  
  function doMdBySync() {
    try {
      let mdAlgName = 'SHA256'; // Digest algorithm name.
      let message = 'mdTestMessage'; // Data to be digested.
      let md = cryptoFramework.createMd(mdAlgName);
      // When the amount of data is small, you can call update only once to pass in all the data at once. The API does not limit the length of the input parameter.
      md.updateSync({ data: new Uint8Array(buffer.from(message, 'utf-8').buffer) });
      let mdResult = md.digestSync();
      console.info('[Sync]:Md result: ' + mdResult.data);
      let mdLen = md.getMdLength();
      console.info('md len: ' + mdLen);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```


### Generating an MD by Passing In Data by Segment

1. Call [cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd) with the MD algorithm **SHA256** to create a message digest (**Md**) instance.

2. Call [Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-7) multiple times to pass in 20 bytes each time.

3. Call [Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest-1) to generate an MD.

4. Call [Md.getMdLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmdlength) to obtain the MD length, in bytes.

- Example: Pass in data by segment to generate an MD using **await**.
  <!-- @[message_digest_sha256_segmentation_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/sha256/segmentation/SegmentationAsync.ets) -->
  
  ``` TypeScript
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  
  async function doLoopMd() {
    try {
      let mdAlgName = 'SHA256'; // digest algorithm name
      let md = cryptoFramework.createMd(mdAlgName);
      // Assume the message is 43 bytes in total, and remains 43 bytes after UTF-8 decoding.
      let messageText = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee';
      let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
      let updateLength = 20; // Assume the data is passed in 20-byte segments for update; there is no actual requirement for this.
      for (let i = 0; i < messageData.length; i += updateLength) {
        let updateMessage = messageData.subarray(i, i + updateLength);
        let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
        await md.update(updateMessageBlob);
      }
      let mdOutput = await md.digest();
      console.info('md result: ' + mdOutput.data);
      let mdLen = md.getMdLength();
      console.info('md len: ' + mdLen);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```


- Example: Pass in data by segment to generate an MD using a synchronous API.

  <!-- @[message_digest_sha256_segmentation_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/sha256/segmentation/SegmentationSync.ets) -->
  
  ``` TypeScript
  
  import { cryptoFramework } from '@kit.CryptoArchitectureKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { buffer } from '@kit.ArkTS';
  
  function doLoopMdBySync() {
    try {
      let mdAlgName = 'SHA256'; // Digest algorithm name.
      let md = cryptoFramework.createMd(mdAlgName);
      // Assume the message is 43 bytes in total, and it is also 43 bytes after UTF-8 decoding.
      let messageText = 'aaaaa.....bbbbb.....ccccc.....ddddd.....eee';
      let messageData = new Uint8Array(buffer.from(messageText, 'utf-8').buffer);
      let updateLength = 20; // Assume update is performed in 20-byte segments. There is no actual requirement for this.
      for (let i = 0; i < messageData.length; i += updateLength) {
        let updateMessage = messageData.subarray(i, i + updateLength);
        let updateMessageBlob: cryptoFramework.DataBlob = { data: updateMessage };
        md.updateSync(updateMessageBlob);
      }
      let mdOutput = md.digestSync();
      console.info('[Sync]:md result: ' + mdOutput.data);
      let mdLen = md.getMdLength();
      console.info('md len: ' + mdLen);
    } catch (err) {
      let e: BusinessError = err as BusinessError;
      console.error(`call failed: errCode: ${e.code}, errMsg: ${e.message}`);
    }
  }
  ```
