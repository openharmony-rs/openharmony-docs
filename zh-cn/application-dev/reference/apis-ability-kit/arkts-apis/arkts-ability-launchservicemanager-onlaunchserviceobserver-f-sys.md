# onLaunchServiceObserver（系统接口）

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## onLaunchServiceObserver

```TypeScript
function onLaunchServiceObserver(observer: LaunchServiceObserver): number
```

注册一个观察者来监听LaunchService状态和进程状态的变化。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function onLaunchServiceObserver(observer: LaunchServiceObserver): int--><!--Device-launchServiceManager-function onLaunchServiceObserver(observer: LaunchServiceObserver): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [LaunchServiceObserver](arkts-ability-launchservicemanager-launchserviceobserver-t-sys.md) | 是 | 用于监听LaunchService状态和进程状态变化的观察者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 注册的观察者ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
| [16000165](../errorcode-ability.md#16000165-应用注册的观察者数量已达到上限) | The number of registered observers for the current application has reached the upper limit. |
