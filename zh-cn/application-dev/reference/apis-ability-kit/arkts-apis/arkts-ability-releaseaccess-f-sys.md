# releaseAccess（系统接口）

## releaseAccess

```TypeScript
function releaseAccess(dataType: DataType): ReleaseStatus
```

以同步方法释放锁屏下指定类型敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当引用计数归零时，密钥可以在锁屏达到系统配置的时长阈值后被销毁。

调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-acquireaccess-f.md#acquireaccess-1)接口成功申请权限后才能使用。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA or ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataType | DataType | 是 | 锁屏下访问的敏感数据类型。dataType需要与acquireAccess接口使用的dataType保持一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ReleaseStatus | 锁屏下敏感数据访问权限的释放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameter is left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found. |
| [29300001](../errorcode-screenLockFileManager.md#29300001-入参错误) | Invalid DataType. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-系统服务工作异常) | The system ability works abnormally. |
| [29300003](../errorcode-screenLockFileManager.md#29300003-应用未开启锁屏敏感数据保护功能) | The application is not enabled the data protection under lock screen. |
| [29300005](../errorcode-screenLockFileManager.md#29300005-未申请锁屏敏感数据访问权限) | File access was not acquired. |

**示例：**

```TypeScript
// 释放锁屏下媒体类型数据的访问权限
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // 释放访问权限
    let releaseStatus = screenLockFileManager.releaseAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (releaseStatus === screenLockFileManager.ReleaseStatus.RELEASE_GRANTED) {
        hilog.info(0x0000, 'testTag', 'releaseAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'releaseAccess failed: %{public}s', message);
}

```

