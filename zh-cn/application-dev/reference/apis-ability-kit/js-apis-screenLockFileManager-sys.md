# @ohos.ability.screenLockFileManager (锁屏敏感数据管理)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->

本模块提供锁屏下应用敏感数据保护的能力，支持申请和释放锁屏下应用敏感数据访问权限，以及查询敏感数据密钥的状态。当敏感数据密钥的引用计数归零，且屏幕被锁定达到系统配置的时长阈值后，密钥会被销毁，此时无法对该数据进行操作。这些密钥只有在屏幕解锁后才能恢复。通过调用本模块的[acquireAccess](#screenlockfilemanageracquireaccess)接口，可以防止密钥在屏幕被锁定达到系统配置的时长阈值后被销毁。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.ability.screenLockFileManager](js-apis-screenLockFileManager.md)。
>
> - 应用开启锁屏下敏感数据保护功能，需在[requestPermissions](../../security/AccessToken/declare-permissions.md#在配置文件中声明权限)中配置权限ohos.permission.PROTECT_SCREEN_LOCK_DATA。

## 导入模块

ArkTS-Dyn示例：
```ts
import { screenLockFileManager } from '@kit.AbilityKit';
```

ArkTS-Sta示例：
```ts
import screenLockFileManager from '@ohos.ability.screenLockFileManager';
```

## screenLockFileManager.acquireAccess

acquireAccess(dataType: DataType): AccessStatus

以同步方法申请锁屏下指定类型的敏感数据访问权限。申请成功后，敏感数据密钥的引用计数增加，防止密钥在锁屏达到系统配置的时长阈值后被销毁。该方法需与[releaseAccess](#screenlockfilemanagerreleaseaccess)配对使用。

调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并通过[queryAppKeyState](#screenlockfilemanagerqueryappkeystate18)接口查询密钥状态为KEY_EXIST。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA 或 ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明                       |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | 是   | 锁屏下访问的敏感数据类型。 |

**返回值：**

| 类型                                                        | 说明                                  |
| ----------------------------------------------------------- | ------------------------------------- |
| [AccessStatus](js-apis-screenLockFileManager.md#accessstatus) | 锁屏下敏感数据访问权限的申请状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏敏感数据管理错误码](errorcode-screenLockFileManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801 | The specified SystemCapability name was not found. |
| 29300001 | Invalid DataType. |
| 29300002 | The system ability works abnormally. |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300004 | File access is denied. |

**示例：**

ArkTS-Dyn示例：
```ts
// 申请锁屏下媒体类型数据的访问权限
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // 申请访问权限
    let acquireStatus = screenLockFileManager.acquireAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (acquireStatus === screenLockFileManager.AccessStatus.ACCESS_GRANTED) {
        hilog.info(0x0000, 'testTag', 'acquireAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'acquireAccess failed: %{public}s', message);
}
```

ArkTS-Sta示例：
```ts
// 申请锁屏下媒体类型数据的访问权限
import screenLockFileManager from '@ohos.ability.screenLockFileManager';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    let acquireStatus = screenLockFileManager.acquireAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (acquireStatus === screenLockFileManager.AccessStatus.ACCESS_GRANTED) {
        hilog.info(0x0000, 'testTag', 'acquireAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'acquireAccess failed: %{public}s', message);
}
```

## screenLockFileManager.releaseAccess

releaseAccess(dataType: DataType): ReleaseStatus

以同步方法释放锁屏下指定类型敏感数据访问权限。释放成功后，敏感数据密钥的引用计数减少，当引用计数归零时，密钥可以在锁屏达到系统配置的时长阈值后被销毁。

调用此接口前，请确保应用已开启锁屏下敏感数据保护功能，并且先调用[acquireAccess](#screenlockfilemanageracquireaccess)接口成功申请权限后才能使用。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA 或 ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明                       |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | 是   | 锁屏下访问的敏感数据类型。dataType需要与acquireAccess接口使用的dataType保持一致。 |

**返回值：**

| 类型                                                         | 说明                           |
| ------------------------------------------------------------ | ------------------------------ |
| [ReleaseStatus](js-apis-screenLockFileManager.md#releasestatus) | 锁屏下敏感数据访问权限的释放状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏敏感数据管理错误码](errorcode-screenLockFileManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | The specified SystemCapability name was not found.           |
| 29300001 | Invalid DataType.                                           |
| 29300002 | The system ability works abnormally.                          |
| 29300003 | The application is not enabled the data protection under lock screen. |
| 29300005 | File access was not acquired.                                |

**示例：**

ArkTS-Dyn示例：
```ts
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

ArkTS-Sta示例：
```ts
// 释放锁屏下媒体类型数据的访问权限
import screenLockFileManager from '@ohos.ability.screenLockFileManager';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    let releaseStatus = screenLockFileManager.releaseAccess(screenLockFileManager.DataType.MEDIA_DATA);
    if (releaseStatus === screenLockFileManager.ReleaseStatus.RELEASE_GRANTED) {
        hilog.info(0x0000, 'testTag', 'releaseAccess successfully.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'releaseAccess failed: %{public}s', message);
}
```

## screenLockFileManager.queryAppKeyState<sup>18+</sup>

queryAppKeyState(dataType: DataType): KeyStatus

以同步方法查询锁屏下指定类型敏感数据密钥的状态。

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_MEDIA_DATA 或 ohos.permission.ACCESS_SCREEN_LOCK_ALL_DATA

**系统能力：** SystemCapability.Security.ScreenLockFileManager

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明                       |
| ----------- | ------ | ---- | ---------------------------- |
| dataType | [DataType](js-apis-screenLockFileManager.md#datatype) | 是   | 锁屏下访问的敏感数据类型。 |

**返回值：**

| 类型                                                         | 说明                           |
| ------------------------------------------------------------ | ------------------------------ |
| [KeyStatus](js-apis-screenLockFileManager.md#keystatus18) | 锁屏下敏感数据密钥的状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏敏感数据管理错误码](errorcode-screenLockFileManager.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed, usually returned by VerifyAccessToken. |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | The specified SystemCapability name was not found.           |
| 29300001 | Invalid DataType.                                           |
| 29300002 | The system ability works abnormally.                          |

**示例：**

ArkTS-Dyn示例：
```ts
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

ArkTS-Sta示例：
```ts
// 查询锁屏下媒体类型数据的访问权限
import screenLockFileManager from '@ohos.ability.screenLockFileManager';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    let keyStatus = screenLockFileManager.queryAppKeyState(screenLockFileManager.DataType.MEDIA_DATA);
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
