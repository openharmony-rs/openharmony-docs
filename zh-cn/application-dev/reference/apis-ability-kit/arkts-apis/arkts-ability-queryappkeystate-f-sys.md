# queryAppKeyState（系统接口）

## queryAppKeyState

```TypeScript
function queryAppKeyState(dataType: DataType): KeyStatus
```

以同步方法查询锁屏下指定类型敏感数据密钥的状态。

**起始版本：** 18

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataType | DataType | 是 | 锁屏下访问的敏感数据类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| KeyStatus | 锁屏下敏感数据密钥的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameter is left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found. |
| [29300001](../errorcode-screenLockFileManager.md#29300001-入参错误) | Invalid DataType. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
// 查询锁屏下媒体类型数据的访问权限
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // 查询密钥状态
    let keyStatus = screenLockFileManager.queryAppKeyState(screenLockFileManager.DataType.MEDIA_DATA);
    // 判断密钥状态并处理不同情况
    if (keyStatus === screenLockFileManager.KeyStatus.KEY_NOT_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key does not exist.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_RELEASED) {
        hilog.info(0x0000, 'testTag', 'Key has been released.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key exists.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'queryAppKeyState failed: %{public}s', message);
}

```

