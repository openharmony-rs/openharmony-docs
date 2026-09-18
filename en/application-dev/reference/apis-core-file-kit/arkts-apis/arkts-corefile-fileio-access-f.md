# access

## Modules to Import

```TypeScript
```

## access

```TypeScript
declare function access(path: string, mode?: number): Promise<void>
```

Checks whether this process can access a file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [access](arkts-corefile-file-fs-access-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| mode | number | No | Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**.<br>The options are as follows:<br>- **0**: Check whether the file exists.<br>- **1**: Check whether the process has the execute permission on the file.<br>- **2**: Check whether the process has the write permission on the file.<br>- **4**: Check whether the process has the read permission on the file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |


## access

```TypeScript
declare function access(path: string, callback: AsyncCallback<void>): void
```

Checks whether this process can access a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [access](arkts-corefile-file-fs-access-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file is asynchronously checked. |


## access

```TypeScript
declare function access(path: string, mode: number, callback: AsyncCallback<void>): void
```

Checks whether this process can access a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [access](arkts-corefile-file-fs-access-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| mode | number | Yes | Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**.<br>The options are as follows:<br>- **0**: Check whether the file exists.<br>- **1**: Check whether the process has the execute permission on the file.<br>- **2**: Check whether the process has the write permission on the file.<br>- **4**: Check whether the process has the read permission on the file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file is asynchronously checked. |
