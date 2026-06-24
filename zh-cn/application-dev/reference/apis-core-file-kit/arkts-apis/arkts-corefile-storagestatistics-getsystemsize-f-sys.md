# getSystemSize（系统接口）

## getSystemSize

```TypeScript
function getSystemSize(callback: AsyncCallback<number>): void
```

异步获取系统数据的空间大小（单位为Byte），以callback方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;number&gt; | 是 | 获取系统数据的空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Mandatory<br/>parameters are left unspecified; |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getSystemSize((error: BusinessError, number: number) => {
  if (error) {
    console.error("getSystemSize failed with error:" + JSON.stringify(error));
  } else {
    // do something
    console.info("getSystemSize successfully:" + number);
  }
});

```


## getSystemSize

```TypeScript
function getSystemSize(): Promise<number>
```

异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回系统数据的空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Mandatory<br/>parameters are left unspecified; |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
storageStatistics.getSystemSize().then((number: number) => {
  console.info("getSystemSize successfully:" + number);
}).catch((err: BusinessError) => {
  console.error("getSystemSize failed with error:" + JSON.stringify(err));
});

```

