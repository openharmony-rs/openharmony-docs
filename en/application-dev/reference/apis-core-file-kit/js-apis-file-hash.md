# @ohos.file.hash (File Hash Processing)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0c20469e58610438940464085fdd62df82c5b560 translatedAt=2026-11-10T05:11:19.668Z pushedAt=2026-11-10T07:37:58.623Z nl=1 -->

This module provides file hash processing capabilities, performing hash processing on file content. It is applicable to scenarios such as data integrity verification, version comparison, and content deduplication, ensuring the immutability and consistency of computation results, and supports streaming processing of large files.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { hash } from '@kit.CoreFileKit';
```

## Guidelines

Before using this functional module to operate on files/directories, you need to obtain the application sandbox path pathDir. For details about how to obtain the sandbox path and the usage of the related APIs, see [Application Context - Obtaining the Application File Path](../../application-models/application-context-stage.md#obtaining-application-file-paths).

## hash.hash

hash(path: string, algorithm: string): Promise&lt;string&gt;

Calculates the hash value of a file, performing hash digest computation on the complete file content based on the specified algorithm. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> This API reads the entire file content and calculates the hash value, and is suitable for small and medium-sized files. For large files, you are advised to use [HashStream](#hashstream12) for streaming computation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name   | Type  | Mandatory| Description                          |
| --------- | ------ | ---- | ------------------------------|
| path      | string | Yes   | Application sandbox path of the file whose hash value is to be calculated. The file must exist and be readable. |
| algorithm | string | Yes  | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes.|

**Return value**

  | Type                   | Description                        |
  | --------------------- | -------------------------- |
  | Promise&lt;string&gt; | Promise object that returns the hash value of the file. It is represented as a hexadecimal digit string, with all letters in uppercase. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900020 | Invalid argument. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
hash.hash(filePath, "sha256").then((str: string) => {
  console.info("Succeeded in calculating file hash: " + str);
}).catch((err: BusinessError) => {
  console.error("Failed to calculate file hash. Code: " + err.code + ", message: " + err.message);
});
```

## hash.hash

hash(path: string, algorithm: string, callback: AsyncCallback&lt;string&gt;): void

Calculates the hash value of a file, performing hash digest computation on the complete file content based on the specified algorithm. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API reads the entire file content and calculates the hash value, and is suitable for small and medium-sized files. For large files, you are advised to use [HashStream](#hashstream12) for streaming computation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name   | Type                       | Mandatory| Description                                                        |
| --------- | --------------------------- | ---- | ------------------------------------------------------------ |
| path      | string                      | Yes   | Application sandbox path of the file whose hash value is to be calculated. The file must exist and be readable.                             |
| algorithm | string                      | Yes  | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes.|
| callback  | AsyncCallback&lt;string&gt; | Yes   | Callback function that returns the hash value (the hash value is represented as a hexadecimal digit string, with all letters in uppercase). |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900020 | Invalid argument. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let filePath = pathDir + "/test.txt";
  hash.hash(filePath, "sha256", (err: BusinessError, str: string) => {
    if (err) {
      console.error("Failed to calculate file hash. Code: " + err.code + ", message: " + err.message);
    } else {
      console.info("Succeeded in calculating file hash: " + str);
    }
  });
  ```
## hash.createHash<sup>12+</sup>

createHash(algorithm: string): HashStream

Creates and returns a HashStream object for generating a hash digest. You can specify the algorithm used for hash calculation. HashStream adopts a streaming processing mechanism and supports updating data in batches, making it suitable for hash calculation of large files or data streams and avoiding loading large files into memory at once.

> **NOTE**
>
> HashStream adopts a streaming processing mechanism and supports updating data in batches, making it suitable for hash calculation of large files or data streams and avoiding loading large files into memory at once.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes.|

**Return value**

| Type           | Description        |
| ------------- | ---------- |
| [HashStream](#hashstream12) | Instance of the HashStream class, used to generate a hash digest. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 401 | Parameter error. |
| 13900020 | Invalid argument. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  // pages/xxx.ets
  import { fileIo } from '@kit.CoreFileKit';

  function hashFileWithStream() {
    const filePath = pathDir + "/test.txt";
    // Create a readable stream.
    const rs = fileIo.createReadStream(filePath);
    // Create a hash stream.
    const hs = hash.createHash('sha256');
    rs.on('data', (emitData) => {
      const data = emitData?.data;
      hs.update(new Uint8Array(data?.split('').map((x: string) => x.charCodeAt(0))).buffer);
    });
    rs.on('close', async () => {
      const hashResult = hs.digest();
      const fileHash = await hash.hash(filePath, 'sha256');
      console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}, fileHash: ${fileHash}`);
    });
  }
  ```


## HashStream<sup>12+</sup>

The HashStream class is a utility for creating a hash digest of data. It is obtained through the [createHash](#hashcreatehash12) API. This class adopts an incremental hash calculation design, adding data blocks multiple times through the update method and finally calculating the final hash value through the digest method. It is suitable for processing large files or continuously generated data streams.

### update<sup>12+</sup>

update(data: ArrayBuffer): void

Updates the hash content with the given data and can be called multiple times. The data from each call is appended to the already calculated hash content, and the complete hash digest is finally obtained through the digest method.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name| Type| Mandatory| Description|
| ---- | ----------- | -- | ----------------- |
| data | ArrayBuffer | Yes | Data for which the hash value is to be calculated, passed in as an ArrayBuffer. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 401 | Parameter error. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  // Create a hash stream.
  const hs = hash.createHash('sha256');
  hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  const hashResult = hs.digest();
  // 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
  console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}`);
  ```

### digest<sup>12+</sup>

digest(): string

Computes the digest of all data passed to the hash processing and returns the final hash value.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Return value**

| Type| Description|
| ------ | --------------------------------------------------------- |
| string | Hash value, which is a hexadecimal string consisting of digits and uppercase letters.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 401 | Parameter error. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  // Create a hash stream.
  const hs = hash.createHash('sha256');
  hs.update(new Uint8Array('1234567890'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  hs.update(new Uint8Array('abcdefg'?.split('').map((x: string) => x.charCodeAt(0))).buffer);
  const hashResult = hs.digest();
  // 88A00F46836CD629D0B79DE98532AFDE3AEAD79A5C53E4848102F433046D0106
  console.info(`Succeeded in calculating file hash. hashResult: ${hashResult}`);
  ```