# OnFileReadyBatch（系统接口）

```TypeScript
type OnFileReadyBatch = (error: BusinessError<void>, files: Array<File>) => void
```

一批文件准备好发送给客户端时触发的回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | BusinessError & lt;void & gt; | 是 | 获取文件句柄失败时返回的错误对象。 |
| files | Array & lt;File & gt; | 是 | 获取到的文件句柄数组。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, backup } from '@kit.CoreFileKit';

const onFileReadyBatch: backup.OnFileReadyBatch = (error: BusinessError<void>, files: Array<backup.File>): void => {
  if (error) {
    console.error(`onFileReadyBatch failed. Code: ${error.code}, message: ${error.message}`);
    return;
  }
  for (let file of files) {
    console.info(`onFileReadyBatch success with file: ${file.bundleName}, ${file.uri}`);
    fileIo.closeSync(file.fd);
  }
};
```
