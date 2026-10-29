# offFocusedApplicationChanged

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## offFocusedApplicationChanged

```TypeScript
function offFocusedApplicationChanged(observerId: number): void
```

注销用于监听获焦应用变化的观察者。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appManager-function offFocusedApplicationChanged(observerId: int): void--><!--Device-appManager-function offFocusedApplicationChanged(observerId: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerId | number | 是 | 已注册观察者的ID，即[onFocusedApplicationChanged](arkts-ability-appmanager-onfocusedapplicationchanged-f.md)返回的监听器ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [16300004](../errorcode-ability.md#16300004-指定的observer不存在) | The observer does not exist. |
