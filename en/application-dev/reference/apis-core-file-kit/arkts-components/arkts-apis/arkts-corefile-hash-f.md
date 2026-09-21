# hash

## Modules to Import

```TypeScript
import { hash } from '@kit.CoreFileKit';
```

## hash

```TypeScript
function hash(path: string, algorithm: string): Promise<string>
```

Calculates a hash value for a file. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file in the application sandbox. |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the hash value. The hash value is a hexadecimal string consisting of digits and uppercase letters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + "/test.txt";
hash.hash(filePath, "sha256").then((str: string) => {
  console.info("calculate file hash succeed:" + str);
}).catch((err: BusinessError) => {
  console.error("calculate file hash failed with error message: " + err.message + ", error code: " + err.code);
});
```


<a id="hash-1"></a>

## hash

```TypeScript
function hash(path: string, algorithm: string, callback: AsyncCallback<string>): void
```

Calculates a hash value for a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file in the application sandbox. |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the hash value obtained. The hash value is a hexadecimal string consisting of digits and uppercase letters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + "/test.txt";
hash.hash(filePath, "sha256", (err: BusinessError, str: string) => {
  if (err) {
    console.error("calculate file hash failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("calculate file hash succeed:" + str);
  }
});
```
