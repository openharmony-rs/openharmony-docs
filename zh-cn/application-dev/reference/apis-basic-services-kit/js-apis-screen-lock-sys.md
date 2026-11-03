# @ohos.screenLock (锁屏管理)(系统接口)
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @jiayunpeng2-->
<!--Designer: @starrylight; @jiayunpeng2-->
<!--Tester: @yaoruijiang-->
<!--Adviser: @fang-jinxu-->

锁屏管理服务是OpenHarmony中的系统服务，为锁屏应用提供注册亮屏、灭屏、开启屏幕、结束休眠、退出动画、请求解锁结果监听，并提供回调结果给锁屏应用。锁屏管理服务向三方应用提供请求解锁、查询锁屏状态、查询是否设置锁屏密码的能力。

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.screenLock (锁屏管理)](js-apis-screen-lock.md)。

## 导入模块

```ts
import { screenLock } from '@kit.BasicServicesKit';
```

## EventType<sup>9+</sup>

type EventType = beginWakeUp | endWakeUp | beginScreenOn | endScreenOn | beginScreenOff | endScreenOff | unlockScreen |
lockScreen | beginExitAnimation | beginSleep | endSleep | changeUser | screenlockEnabled | serviceRestart |
strongAuthChanged | screenLockDisabledChanged | unlockPolicyChanged

定义系统事件类型。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

| 类型            | 说明                     |
| ------------------ | ------------------------ |
| beginWakeUp        | 表示设备开始唤醒。 |
| endWakeUp          | 表示设备结束唤醒。 |
| beginScreenOn      | 表示设备开始亮屏。 |
| endScreenOn        | 表示设备结束亮屏。 |
| beginScreenOff     | 表示设备开始灭屏。 |
| endScreenOff       | 表示设备结束灭屏。 |
| unlockScreen       | 表示请求屏幕解锁。       |
| lockScreen         | 表示请求屏幕锁定。       |
| beginExitAnimation | 表示开始退场动画。       |
| beginSleep         | 表示设备开始休眠。           |
| endSleep           | 表示设备结束休眠。           |
| changeUser         | 表示切换用户。           |
| screenlockEnabled  | 表示锁屏是否启用。       |
| serviceRestart     | 表示锁屏服务进行重启。   |
| strongAuthChanged  | 表示锁屏增强认证状态变化时候的事件类型。       |
| screenLockDisabledChanged     | 表示锁屏被禁用、启用状态变化时候的事件类型。   |
| unlockPolicyChanged     | 表示锁屏解锁策略变化时候的事件类型。<br> **起始版本：** 26.0.0   |

## SystemEvent<sup>9+</sup>

定义系统事件回调参数结构。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

| 名称    | 类型   | 只读 | 可选 |       说明        |
| --------- | ------ | ---- | ---- | ------------- |
| eventType   | [EventType](#eventtype9) | 否   | 否   | 系统事件类型。 |
| params | string | 否   | 否   | 系统事件参数。 |

## StrongAuthReasonFlags<sup>12+</sup>

表示请求强认证的原因标志位。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NONE | 0x00000000 | 表示无强认证。 |
| AFTER_BOOT | 0x00000001 | 表示开机后强认证。 |
| AFTER_TIMEOUT | 0x00000002 | 表示超时强认证。 |
| ACTIVE_REQUEST | 0x00000004 | 表示主动请求强认证。 |
| POLICY_RESTRICTION | 0x00000008 | 表示策略限制请求强认证。 |

## AuthState<sup>12+</sup>

表示锁屏认证状态的枚举。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| NOT_AUTHED | 0 | 表示锁屏未认证。 |
| PRE_AUTHED_BY_CREDENTIAL | 1 | 表示锁屏通过凭据预认证。 |
| PRE_AUTHED_BY_FINGERPRINT | 2 | 表示锁屏通过指纹预认证。 |
| PRE_AUTHED_BY_FACE | 3 | 表示锁屏通过人脸预认证。 |
| AUTHED_BY_CREDENTIAL | 4 | 表示锁屏通过凭据认证。 |
| AUTHED_BY_FINGERPRINT | 5 | 表示锁屏通过指纹认证。 |
| AUTHED_BY_FACE | 6 | 表示锁屏通过人脸认证。 |

## UnlockPolicy

表示解锁屏幕所使用的锁屏认证策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| DEFAULT | 0 | 表示使用默认系统认证方式解锁锁屏。 |
| EXTENDED_AUTH_ONLY | 1 | 表示仅使用扩展认证方式解锁锁屏。 |
| EXTENDED_AUTH_AND_SYSTEM | 2 | 表示使用扩展认证和系统认证方式解锁锁屏。 |

## screenLock.isLocked<sup>9+</sup>

isLocked(): boolean

判断屏幕是否锁屏。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

**返回值：** 

| 类型    | 说明                                              |
| ------- | ------------------------------------------------- |
| boolean | 表示屏幕是否锁屏，返回true表示屏幕已锁屏；返回false表示屏幕未锁屏。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 202  | permission verification failed, application which is not a system application uses system API.         |

**示例：** 

```ts
let isLocked = screenLock.isLocked();
```

## screenLock.unlock<sup>9+</sup>

unlock(callback: AsyncCallback&lt;boolean&gt;): void

解锁屏幕。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

**参数：** 

| 参数名   | 类型          | 必填 | 说明                                 |
| -------- | --------------------- | ---- | ------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。返回true表示屏幕解锁成功；返回false表示取消解锁。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |
| 13200003  | Invalid use.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.unlock((err: BusinessError, data: Boolean) => {
    if (err) {
      console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in unlocking the screen. result: ${data}`);
  });
  ```

> **说明：**
>
> 在 api11 中 增加错误码`13200003 Invalid use` 。

## screenLock.unlock<sup>9+</sup>

unlock(): Promise&lt;boolean&gt;

解锁屏幕。使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

**返回值：** 

| 类型                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示屏幕解锁成功；返回false表示取消解锁。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |
| 13200003  | Invalid use.       |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.unlock().then((data: Boolean) => {
    console.info(`Succeeded in unlocking the screen. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
  });
  ```

> **说明：**
>
> 在 api11 中 增加错误码`13200003 Invalid use` 。

## screenLock.lock<sup>9+</sup>

lock(callback: AsyncCallback&lt;boolean&gt;): void

锁定屏幕。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**参数：** 

| 参数名   | 类型          | 必填 | 说明                      |
| -------- | ---------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。返回true表示屏幕锁定成功；返回false表示屏幕锁定失败。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.lock((err: BusinessError, data: Boolean) => {
    if (err) {
      console.error(`Failed to lock the screen, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in locking the screen. result: ${data}`);
  });
  ```

## screenLock.lock<sup>9+</sup>

lock(): Promise&lt;boolean&gt;

锁定屏幕。使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**返回值：** 

| 类型                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise对象。返回true表示屏幕锁定成功；返回false表示屏幕锁定失败。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.lock().then((data: Boolean) => {
    console.info(`Succeeded in locking the screen. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to lock the screen, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## screenLock.onSystemEvent<sup>9+</sup>

onSystemEvent(callback: Callback&lt;SystemEvent&gt;): boolean

注册锁屏相关的系统事件，仅支持锁屏应用使用。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**参数：** 

| 参数名   | 类型                        | 必填 | 说明               |
| -------- | ------------------------- | ---- | ----------------- |
| callback | Callback\<[SystemEvent](#systemevent9)> | 是   | 锁屏相关的系统事件回调函数。 |

**返回值：** 

| 类型    | 说明                                              |
| ------- | ------------------------------------------------- |
| boolean | 表示锁屏相关系统事件注册是否成功，返回true表示锁屏相关系统事件注册成功；返回false表示锁屏相关系统事件注册失败。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    let isSuccess = screenLock.onSystemEvent((event: screenLock.SystemEvent) => {
      console.info(`Succeeded in Registering the system event which related to screenlock. eventType: ${event.eventType}`);
    });
  } catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to register the system event which related to screenlock, Code: ${error.code}, message: ${error.message}`);
  }
  ```

## screenLock.sendScreenLockEvent<sup>9+</sup>

sendScreenLockEvent(event: String, parameter: number, callback: AsyncCallback&lt;boolean&gt;): void

应用发送事件到锁屏服务，仅支持锁屏应用使用。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**参数：** 

| 参数名    | 类型            | 必填 | 说明                                                                                                                |
| --------- | ------------------------ | ---- |-------------------------------------------------------------------------------------------------------------------|
| event     | String                   | 是   | 事件类型，支持如下取值：<br/>- "unlockScreenResult"，表示解锁结果。<br/>- "lockScreenResult"，表示锁屏结果。<br/>- "screenDrawDone"，表示屏幕绘制完成。 |
| parameter | number                   | 是   | 事件结果。<br/>- parameter为0，表示成功。例如解锁成功或锁屏成功。<br/>- parameter为1，表示失败。例如解锁失败或锁屏失败。<br/>- parameter为2，表示取消。例如锁屏取消或解锁取消。 |
| callback  | AsyncCallback\<boolean> | 是   | 回调函数。返回true表示发送事件成功；返回false表示发送事件失败。                                                                              |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  |the screenlock management service is abnormal.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.sendScreenLockEvent('unlockScreenResult', 0, (err: BusinessError, result: Boolean) => {
    if (err) {
      console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in Sending screenlock event. result: ${result}`);
  });
  ```

## screenLock.sendScreenLockEvent<sup>9+</sup>

sendScreenLockEvent(event: String, parameter: number): Promise&lt;boolean&gt;

应用发送事件到锁屏服务，仅支持锁屏应用使用。使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**参数：** 

| 参数名    | 类型   | 必填 | 说明                                                                                                                |
| --------- | ------ | ---- |-------------------------------------------------------------------------------------------------------------------|
| event     | String | 是   | 事件类型，支持如下取值：<br/>- "unlockScreenResult"，表示解锁结果。<br/>- "lockScreenResult"，表示锁屏结果。<br/>- "screenDrawDone"，表示屏幕绘制完成。 |
| parameter | number | 是   | 事件结果。<br/>- parameter为0，表示成功。例如解锁成功或锁屏成功。<br/>- parameter为1，表示失败。例如解锁失败或锁屏失败。<br/>- parameter为2，表示取消。例如锁屏取消或解锁取消。 |

**返回值：** 

| 类型               | 说明                                           |
| ----------------- | ---------------------------------------------- |
| Promise\<boolean> | Promise对象。返回true表示发送事件成功；返回false表示发送事件失败。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**示例：** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.sendScreenLockEvent('unlockScreenResult', 0).then((result: Boolean) => {
    console.info(`Succeeded in Sending screenlock event. result: ${result}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## screenLock.requestStrongAuth<sup>12+</sup>

requestStrongAuth(reasonFlag: StrongAuthReasonFlags, userId: number): Promise&lt;void&gt;

为指定用户请求强认证。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| reasonFlag | [StrongAuthReasonFlags](#strongauthreasonflags12) | 是 | 强认证原因标志位。 |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed. A non-system application calls a system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.requestStrongAuth(screenLock.StrongAuthReasonFlags.AFTER_BOOT, 100).then(() => {
  console.info('Succeeded in requesting strong auth.');
}).catch((err: BusinessError) => {
  console.error(`Failed to request strong auth, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.getStrongAuth<sup>12+</sup>

getStrongAuth(userId: number): number

获取指定用户的强认证原因标志位。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 强认证原因标志位。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed. A non-system application calls a system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
let strongAuth = screenLock.getStrongAuth(100);
console.info(`Strong auth flags: ${strongAuth}`);
```

## screenLock.setScreenLockDisabled<sup>12+</sup>

setScreenLockDisabled(disable: boolean, userId: number): Promise&lt;boolean&gt;

为指定用户禁用或启用锁屏。仅在未设置密码时生效。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| disable | boolean | 是 | 表示是否禁用锁屏，true表示禁用锁屏，false表示启用锁屏。 |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设置成功；返回false表示设置失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.setScreenLockDisabled(true, 100).then((result: boolean) => {
  console.info(`Succeeded in setting screen lock disabled. result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen lock disabled, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.isScreenLockDisabled<sup>12+</sup>

isScreenLockDisabled(userId: number): boolean

查询指定用户的锁屏是否被禁用。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 表示锁屏是否被禁用，返回true表示锁屏已禁用；返回false表示锁屏未禁用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
let isDisabled = screenLock.isScreenLockDisabled(100);
console.info(`Screen lock disabled: ${isDisabled}`);
```

## screenLock.setScreenLockAuthState<sup>12+</sup>

setScreenLockAuthState(state: AuthState, userId: number, authToken: Uint8Array): Promise&lt;boolean&gt;

为指定用户设置锁屏认证状态。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| state | [AuthState](#authstate12) | 是 | 锁屏认证状态。 |
| userId | number | 是 | 用户ID。 |
| authToken | Uint8Array | 是 | 该状态对应的认证令牌。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示设置成功；返回false表示设置失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let authToken = new Uint8Array([1, 2, 3, 4]);
screenLock.setScreenLockAuthState(screenLock.AuthState.AUTHED_BY_CREDENTIAL, 100, authToken).then((result: boolean) => {
  console.info(`Succeeded in setting screen lock auth state. result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen lock auth state, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.getScreenLockAuthState<sup>12+</sup>

getScreenLockAuthState(userId: number): AuthState

获取指定用户的锁屏认证状态。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [AuthState](#authstate12) | 锁屏认证状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**示例：**

```ts
let authState = screenLock.getScreenLockAuthState(100);
console.info(`Screen lock auth state: ${authState}`);
```

## screenLock.isDeviceLocked<sup>20+</sup>

isDeviceLocked(userId: number): boolean

查询设备是否已锁屏且需要身份认证才能解锁。

**系统能力：** SystemCapability.MiscServices.ScreenLock

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 表示设备是否锁屏，返回true表示设备已锁屏；返回false表示设备未锁屏。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 13200002 | The screenlock management service is abnormal. |
| 13200004 | The userId is not same as the caller, and is not allowed for the caller. |

**示例：**

```ts
let isDeviceLocked = screenLock.isDeviceLocked(100);
console.info(`Device locked: ${isDeviceLocked}`);
```

## screenLock.getUnlockPolicy

getUnlockPolicy(userId: number): UnlockPolicy

获取解锁屏幕所使用的认证策略。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.MiscServices.ScreenLock

**需要权限：** ohos.permission.ACCESS_SCREEN_LOCK

**系统接口**：此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [UnlockPolicy](#unlockpolicy) | 解锁策略。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[锁屏服务错误码](errorcode-screenlock.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Permission verification failed: applications that are not system applications cannot use system API. |
| 13200002 | The screen lock management service is abnormal. |
| 13200004 | The userId is not the same as the caller, and the caller is not authorized. |

**示例：**

```ts
let unlockPolicy = screenLock.getUnlockPolicy(100);
console.info(`Unlock policy: ${unlockPolicy}`);
```

