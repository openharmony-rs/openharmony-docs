# listUserdataDirInfo（系统接口）

## listUserdataDirInfo

```TypeScript
function listUserdataDirInfo(): Promise<Array<UserdataDirInfo>>
```

查询用户设备中/data目录下的空间占用详情，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.STORAGE_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;UserdataDirInfo&gt;&gt; | Promise对象，返回用户设备中/data目录下的空间占用详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600015 | Failed to traverse the query data partition directory. |

**示例：**

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.listUserdataDirInfo().then((dirInfos: storageStatistics.UserdataDirInfo[]) => {
  console.info("listUserdataDirInfo successfully.");
}).catch((err: BusinessError) => {
  console.error(`listUserdataDirInfo failed with err, code is: ${err.code}, message is: ${err.message}`);
});

```

