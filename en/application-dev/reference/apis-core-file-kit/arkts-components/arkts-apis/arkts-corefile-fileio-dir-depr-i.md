# Dir

```TypeScript
declare interface Dir
```

Manages directories. Before calling a method of the **Dir** class, use the **opendir()** method synchronously or asynchronously to create a **Dir** instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
```

## close

```TypeScript
close(): Promise<void>
```

Closes a directory. This API uses a promise to return the result. After a directory is closed, the file descriptor in **Dir** will be released and no directory entry can be read from **Dir**.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | return Promise |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.close().then(() => {
  console.info("close dir successfully");
});
```

<a id="close-1"></a>

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

Closes a directory. This API uses an asynchronous callback to return the result. After a directory is closed, the file descriptor in **Dir** will be released and no directory entry can be read from **Dir**.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | callback. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.close((err: BusinessError) => {
  console.info("close dir successfully");
});
```

## closeSync

```TypeScript
closeSync(): void
```

Closes a directory. After a directory is closed, the file descriptor in **Dir** will be released and no directory entry can be read from **Dir**.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Examples**

```TypeScript
dir.closeSync();
```

## read

```TypeScript
read(): Promise<Dirent>
```

Reads the next directory entry. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Dirent](arkts-corefile-fileio-dirent-depr-i.md)&gt; | Promise that returns the next directory entry. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.read().then((dirent: fileio.Dirent) => {
  console.info("read succeed, the name of dirent is " + dirent.name);
}).catch((err: BusinessError) => {
  console.error("read failed with error:" + err);
});
```

<a id="read-1"></a>

## read

```TypeScript
read(callback: AsyncCallback<Dirent>): void
```

Reads the next directory entry. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Dirent](arkts-corefile-fileio-dirent-depr-i.md)&gt; | Yes | Callback invoked when the next directory entry is asynchronously read. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.read((err: BusinessError, dirent: fileio.Dirent) => {
  if (dirent) {
    // Do something.
    console.info("read succeed, the name of file is " + dirent.name);
  }
});
```

## readSync

```TypeScript
readSync(): Dirent
```

Reads the next directory entry. This API returns the result synchronously.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| [Dirent](arkts-corefile-fileio-dirent-depr-i.md) | Directory entry read. |

**Examples**

```TypeScript
let dirent = dir.readSync();
```
