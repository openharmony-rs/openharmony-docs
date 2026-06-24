# optimizeStorage（系统接口）

## optimizeStorage

```TypeScript
function optimizeStorage():Promise<void>
```

�Ż�ͼ����ͬ���ƿռ�ı�����Դ�����ձ���ʣ��ռ�ִ���Զ��ϻ����ԡ�ʹ��Promise�첽�ص���

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API.<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudSync.optimizeStorage().then(() => {
  console.info("optimize storage successfully");   // 前台UX按需阻塞等待
}).catch((err: BusinessError) => {
  console.error("optimize storage failed with error message: " + err.message + ", error code: " + err.code);
});

```

