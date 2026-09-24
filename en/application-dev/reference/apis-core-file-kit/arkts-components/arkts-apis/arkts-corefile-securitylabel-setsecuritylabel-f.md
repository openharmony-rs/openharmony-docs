# setSecurityLabel

## Modules to Import

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## setSecurityLabel

```TypeScript
function setSecurityLabel(path: string, type: DataLevel): Promise<void>
```

Sets the data security level for a file or directory. The level can only be adjusted from low to high, or set to the same level. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |
| type | [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | Yes | Data security level. The value can only be **s0**, **s1**, **s2**, **s3**, or **s4**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
securityLabel.setSecurityLabel(filePath, "s0").then(() => {
  console.info("setSecurityLabel successfully");
}).catch((err: BusinessError) => {
  console.error("setSecurityLabel failed with error message: " + err.message + ", error code: " + err.code);
});
```


<a id="setsecuritylabel-1"></a>

## setSecurityLabel

```TypeScript
function setSecurityLabel(path: string, type: DataLevel, callback: AsyncCallback<void>): void
```

Sets the data security level for a file or directory. The level can only be adjusted from low to high, or set to the same level. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | File path. |
| type | [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | Yes | Data security level. The value can only be **s0**, **s1**, **s2**, **s3**, or **s4**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the security level. |

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
securityLabel.setSecurityLabel(filePath, "s0", (err: BusinessError) => {
  if (err) {
    console.error("setSecurityLabel failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("setSecurityLabel successfully.");
  }
});
```
