# Dir

管理目录，在调用Dir的方法前，需要先通过opendir方法（同步或异步）来构建一个Dir实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-unnamed-declare interface Dir--><!--Device-unnamed-declare interface Dir-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## close

```TypeScript
close(): Promise<void>
```

异步关闭目录，使用promise形式返回结果。目录被关闭后，Dir中持有的文件描述将被释放，后续将无法从Dir中读取目录项。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-close(): Promise<void>--><!--Device-Dir-close(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | return Promise |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.close().then(() => {
  console.info("close dir successfully");
});

```

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

异步关闭目录，使用callback形式返回结果。目录被关闭后，Dir中持有的文件描述将被释放，后续将无法从Dir中读取目录项。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-close(callback: AsyncCallback<void>): void--><!--Device-Dir-close(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | callback. |

**示例：**

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

用于关闭目录。目录被关闭后，Dir中持有的文件描述将被释放，后续将无法从Dir中读取目录项。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-closeSync(): void--><!--Device-Dir-closeSync(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**示例：**

```TypeScript
dir.closeSync();

```

## read

```TypeScript
read(): Promise<Dirent>
```

读取下一个目录项，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-read(): Promise<Dirent>--><!--Device-Dir-read(): Promise<Dirent>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Dirent> | Promise对象。返回表示异步读取目录项的结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.read().then((dirent: fileio.Dirent) => {
  console.info("read succeed, the name of dirent is " + dirent.name);
}).catch((err: BusinessError) => {
  console.error("read failed with error:" + err);
});

```

## read

```TypeScript
read(callback: AsyncCallback<Dirent>): void
```

读取下一个目录项，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-read(callback: AsyncCallback<Dirent>): void--><!--Device-Dir-read(callback: AsyncCallback<Dirent>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Dirent> | 是 | 异步读取下一个目录项之后的回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
dir.read((err: BusinessError, dirent: fileio.Dirent) => {
  if (dirent) {
    // do something
    console.info("read succeed, the name of file is " + dirent.name);
  }
});

```

## readSync

```TypeScript
readSync(): Dirent
```

同步读取下一个目录项。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dir-readSync(): Dirent--><!--Device-Dir-readSync(): Dirent-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Dirent](arkts-corefile-fileio-dirent-depr-i.md) | 表示一个目录项。 |

**示例：**

```TypeScript
let dirent = dir.readSync();

```

