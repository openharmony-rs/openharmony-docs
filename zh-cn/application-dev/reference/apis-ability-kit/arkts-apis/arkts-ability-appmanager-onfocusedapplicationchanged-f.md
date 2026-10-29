# onFocusedApplicationChanged

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## onFocusedApplicationChanged

```TypeScript
function onFocusedApplicationChanged(observer: FocusedApplicationObserver): number
```

注册观察者以监听获焦应用变化。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appManager-function onFocusedApplicationChanged(observer: FocusedApplicationObserver): int--><!--Device-appManager-function onFocusedApplicationChanged(observer: FocusedApplicationObserver): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [FocusedApplicationObserver](arkts-ability-appmanager-focusedapplicationobserver-t.md) | 是 | 用于监听获焦应用变化的观察者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 已注册观察者的ID，可以通过[offFocusedApplicationChanged](arkts-ability-appmanager-offfocusedapplicationchanged-f.md)传入该ID来注销观察者。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [16000165](../errorcode-ability.md#16000165-应用注册的观察者数量已达到上限) | The number of registered observers for the current application has reached the upper limit. |
