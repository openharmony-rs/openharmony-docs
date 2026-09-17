# readText

## Modules to Import

```TypeScript
```

## readText

```TypeScript
declare function readText(
  filePath: string,
  options?: {
    position?: number;
    length?: number;
    encoding?: string;
  }
): Promise<string>
```

Reads the text content of a file. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readText](arkts-corefile-file-fs-readtext-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file to read. |
| options | {     position?: number;     length?: number;     encoding?: string;   } | No | The options are as follows:<br>- **position** (number): position of the data to read in the file, in bytes. This parameter is optional. By default, data is read from the current position.<br>- **length** (number): length of the data to read, in bytes. This parameter is optional. The default value is the buffer length minus the offset.<br>- **encoding** (string): format of the data to be encoded.<br>It is valid only when the data is of the string type.<br>The default value is **'utf-8'**, which is the only value supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise that returns the file content read. |


## readText

```TypeScript
declare function readText(
  filePath: string,
  options: {
    position?: number;
    length?: number;
    encoding?: string;
  },
  callback: AsyncCallback<string>
): void
```

Reads the text content of a file. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [readText](arkts-corefile-file-fs-readtext-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file to read. |
| options | {     position?: number;     length?: number;     encoding?: string;   } | Yes | The options are as follows:<br>- **position** (number): position of the data to read in the file, in bytes. This parameter is optional. By default, data is read from the current position.<br>- **length** (number): length of the data to read, in bytes. This parameter is optional. The default value is the buffer length minus the offset.<br>- **encoding**: format of the data to be encoded. The default value is **'utf-8'**, which is the only value supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the file content read. |
