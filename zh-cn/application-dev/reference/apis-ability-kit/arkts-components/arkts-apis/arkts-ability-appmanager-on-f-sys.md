# on（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## on('applicationState')

```TypeScript
function on(type: 'applicationState', observer: ApplicationStateObserver, filter: AppStateFilter): number
```

注册应用程序的状态监听器，并通过设置过滤条件来筛选所需监听的应用生命周期变化事件。

**起始版本：** 21

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'applicationState' | 是 | 调用接口类型，固定填'applicationState'字符串。 |
| observer | [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | 是 | 应用状态监听器，用于监听应用的生命周期变化。 |
| filter | [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) | 是 | 应用生命周期变化事件的过滤器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已注册监听器ID，可用于off接口注销监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |


## on('appForegroundState')

```TypeScript
function on(type: 'appForegroundState', observer: AppForegroundStateObserver): void
```

注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。

**起始版本：** 11

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appForegroundState' | 是 | 调用接口类型，固定填'appForegroundState'字符串。 |
| observer | [AppForegroundStateObserver](arkts-ability-appmanager-appforegroundstateobserver-t-sys.md) | 是 | 应用状态监听器，用于监听应用的启动和退出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


## on('abilityFirstFrameState')

```TypeScript
function on(type: 'abilityFirstFrameState', observer: AbilityFirstFrameStateObserver, bundleName?: string): void
```

注册监听Ability首帧绘制完成事件观察者对象，可用于系统应用监听Ability首帧绘制事件。

**起始版本：** 12

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityFirstFrameState' | 是 | 调用接口类型，固定填'abilityFirstFrameState'字符串。 |
| observer | [AbilityFirstFrameStateObserver](arkts-ability-appmanager-abilityfirstframestateobserver-t-sys.md) | 是 | 表示待注册的Ability首帧绘制完成事件观察者对象。 |
| bundleName | string | 否 | 表示待监听的Ability的应用bundleName，不填表示注册监听所有应用ability首帧绘制完成事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
