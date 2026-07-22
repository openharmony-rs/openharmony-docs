# fileSystemServiceRequest（系统接口）

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## fileSystemServiceRequest

```TypeScript
function fileSystemServiceRequest(config: FileSystemRequestConfig): Promise<number>
```

根据指定配置请求文件系统执行碎片清理。

**起始版本：** 23

**需要权限：** ohos.permission.BACKUP

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backup-function fileSystemServiceRequest(config: FileSystemRequestConfig): Promise<int>--><!--Device-backup-function fileSystemServiceRequest(config: FileSystemRequestConfig): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [FileSystemRequestConfig](arkts-corefile-backup-filesystemrequestconfig-i-sys.md) | 是 | 碎片清理的配置参数。<br>triggerType取值为0，writeSize取值范围为0至2097152 MB，waitTime取值范围为0至300秒。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回碎片清理的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| 13900020 | Invalid argument |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

async function testFunction(size: number) {
  try {
    const result = await backup.fileSystemServiceRequest({
      triggerType: 0,
      writeSize: size,
      waitTime: 180
    });
    console.info(`fileSystemServiceRequest result: ${result}`);
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`fileSystemServiceRequest err:` + err);
  }
}

```

