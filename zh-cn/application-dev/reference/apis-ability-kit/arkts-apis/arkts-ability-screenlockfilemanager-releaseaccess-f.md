# releaseAccess

## 导入模块

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

<a id="releaseaccess"></a>
## releaseAccess

```TypeScript
function releaseAccess(): ReleaseStatus
```

以同步方法释放调用方应用锁屏下敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当计数归零时，密钥可以在屏幕被锁定达到系统配置的时长阈值后被销毁。

调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](arkts-ability-screenlockfilemanager-acquireaccess-f.md#acquireaccess-1)接口成功申请权限后才能使用。

**起始版本：** 12

<!--Device-screenLockFileManager-function releaseAccess(): ReleaseStatus--><!--Device-screenLockFileManager-function releaseAccess(): ReleaseStatus-End-->

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReleaseStatus](arkts-ability-screenlockfilemanager-releasestatus-e.md) | 锁屏下敏感数据访问权限的释放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-系统服务工作异常) | The system ability works abnormally. |
| [29300003](../errorcode-screenLockFileManager.md#29300003-应用未开启锁屏敏感数据保护功能) | The application is not enabled the data protection under lock screen. |
| [29300005](../errorcode-screenLockFileManager.md#29300005-未申请锁屏敏感数据访问权限) | File access was not acquired. |

**示例：**

```TypeScript
// 释放锁屏下应用敏感数据访问权限
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // 释放访问权限
    let releaseStatus = screenLockFileManager.releaseAccess();
    if (releaseStatus === screenLockFileManager.ReleaseStatus.RELEASE_GRANTED) {
        hilog.info(0x0000, 'testTag', 'releaseAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'releaseAccess failed: %{public}s', message);
}

```

