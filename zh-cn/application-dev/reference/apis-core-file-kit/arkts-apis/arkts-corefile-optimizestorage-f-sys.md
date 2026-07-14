# optimizeStorage（系统接口）

## optimizeStorage

```TypeScript
function optimizeStorage():Promise<void>
```

优化图库已同步云空间的本地资源，按照本地剩余空间执行自动老化策略。使用Promise异步回调。

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application usessystem API.<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudSync.optimizeStorage().then(() => {
  console.info("optimize storage successfully");   // 前台UX按需阻塞等待
}).catch((err: BusinessError) => {
  console.error(`optimize storage failed with error message: ${err.message}, error code: ${err.code}`);
});

```

