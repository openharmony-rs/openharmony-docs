# getSecurityLabel

## Modules to Import

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## getSecurityLabel

```TypeScript
function getSecurityLabel(path: string): Promise<string>
```

Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the data security level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.getSecurityLabel(filePath).then((type: string) => {
  console.info("getSecurityLabel successfully, Label: " + type);
}).catch((err: BusinessError) => {
  console.error("getSecurityLabel failed with error message: " + err.message + ", error code: " + err.code);
});
```


<a id="getsecuritylabel-1"></a>

## getSecurityLabel

```TypeScript
function getSecurityLabel(path: string, callback: AsyncCallback<string>): void
```

Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback after the data security level is obtained asynchronously. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let filePath = pathDir + '/test.txt';
securityLabel.getSecurityLabel(filePath, (err: BusinessError, type: string) => {
  if (err) {
    console.error("getSecurityLabel failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("getSecurityLabel successfully, Label: " + type);
  }
});
```
