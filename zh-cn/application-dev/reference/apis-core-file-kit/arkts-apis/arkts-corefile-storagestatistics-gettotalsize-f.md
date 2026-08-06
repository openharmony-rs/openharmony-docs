# getTotalSize

## getTotalSize

```TypeScript
function getTotalSize(callback: AsyncCallback<long>): void
```

获取内置存储的总空间大小（单位为Byte），以callback方式返回。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本9 - 14：ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getTotalSize(callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getTotalSize(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;long&gt; | 是 | 获取内置存储的总空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 14 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let error: BusinessError = {};
let totalSize: long = 0;
storageStatistics.getTotalSize((error, totalSize) => {
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
function getTotalSize(): Promise<long>
```

获取内置存储的总空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-storageStatistics-function getTotalSize(): Promise<long>--><!--Device-storageStatistics-function getTotalSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回内置存储的总空间大小（单位为Byte）。 (Unit: Byte) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalSize().then((totalSize: number) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError) => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let totalSize: long = 0;
storageStatistics.getTotalSize().then((totalSize) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError): void => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

