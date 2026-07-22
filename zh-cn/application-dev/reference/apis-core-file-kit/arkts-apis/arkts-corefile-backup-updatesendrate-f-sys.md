# updateSendRate（系统接口）

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## updateSendRate

```TypeScript
function updateSendRate(bundleName: string, sendRate: number): boolean
```

更新备份应用发送文件描述符的速率。

**起始版本：** 12

**需要权限：** ohos.permission.BACKUP

<!--Device-backup-function updateSendRate(bundleName: string, sendRate: int): boolean--><!--Device-backup-function updateSendRate(bundleName: string, sendRate: int): boolean-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要控制文件描述符发送速率的应用名称。 |
| sendRate | number | 是 | 文件描述符发送速率，单位为个/秒，取值范围为0至800。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设置结果，true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backup } from '@kit.CoreFileKit';

function updateSendRate() {
  try {
    let bundleName = 'com.example.myApp';
    let sendRate = 300;
    let result = backup.updateSendRate(bundleName, sendRate);
    if (result) {
      console.info('updateSendRate success');
    } else {
      console.info('updateSendRate fail');
    }
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`updateSendRate failed. Code: ${err.code}, message: ${err.message}`);
  }
}

```

