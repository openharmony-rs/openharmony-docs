# getTotalSize（系统接口）

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getTotalSize

```TypeScript
function getTotalSize(callback: AsyncCallback<number>): void
```

获取内置存储的总空间大小（单位为Byte），以callback方式返回。

**起始版本：** 15

**需要权限：** 
- API版本9 - 14：ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getTotalSize(callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getTotalSize(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 获取内置存储的总空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>**适用版本：** 9 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.<br>**适用版本：** 9 - 14 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize((error: BusinessError, totalSize: number) => {
  if (error) {
    console.error(`getTotalSize failed. Code: ${error.code}, message: ${error.message}`);
  } else {
    // do something
    console.info('getTotalSize successfully:' + totalSize);
  }
});

```

