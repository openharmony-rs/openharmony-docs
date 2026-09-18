# stat

## Modules to Import

```TypeScript
```

## stat

```TypeScript
declare function stat(path: string): Promise<Stat>
```

Obtains file information. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stat](arkts-corefile-file-fs-stat-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Promise that returns the file information obtained. |


## stat

```TypeScript
declare function stat(path: string, callback: AsyncCallback<Stat>): void
```

Obtains file information. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stat](arkts-corefile-file-fs-stat-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-fileio-stat-depr-i.md)&gt; | Yes | Callback used to return the file information obtained. |
