# getTotalSize

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

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 获取内置存储的总空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>**适用版本：** 9 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.<br>**适用版本：** 9 - 14 |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例**

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


## getTotalSize

```TypeScript
function getTotalSize(): Promise<number>
```

获取内置存储的总空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 15

**需要权限：** 
- API版本9 - 14：ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回内置存储的总空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>**适用版本：** 9 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.<br>**适用版本：** 9 - 14 |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getTotalSize().then((totalSize: number) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError) => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```
