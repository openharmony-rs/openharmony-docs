# getSystemSize（系统接口）

## getSystemSize

```TypeScript
function getSystemSize(callback: AsyncCallback<long>): void
```

异步获取系统数据的空间大小（单位为Byte），以callback方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getSystemSize(callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getSystemSize(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 获取系统数据的空间大小之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemSize((error: BusinessError, systemSize: number) => {
  if (error) {
    console.error(`getSystemSize failed with err, code is: ${error.code}, message is: ${error.message}`);
  } else {
    // do something
    console.info("getSystemSize successfully:" + systemSize);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemSize((error: BusinessError, systemSize: long): void => {
  if (error) {
    console.error(`getSystemSize failed with err, code is: ${error.code}, message is: ${error.message}`);
  } else {
    // do something
    console.info("getSystemSize successfully:" + systemSize);
  }
});
```


## getSystemSize

```TypeScript
function getSystemSize(): Promise<long>
```

异步获取系统数据的空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getSystemSize(): Promise<long>--><!--Device-storageStatistics-function getSystemSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回系统数据的空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemSize().then((systemSize: number) => {
  console.info("getSystemSize successfully:" + systemSize);
}).catch((err: BusinessError) => {
  console.error(`getSystemSize failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemSize().then((systemSize: long) => {
  console.info("getSystemSize successfully:" + systemSize);
}).catch((err: BusinessError): void => {
  console.error(`getSystemSize failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

