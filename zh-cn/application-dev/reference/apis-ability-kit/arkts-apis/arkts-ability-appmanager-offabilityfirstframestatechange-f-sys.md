# offAbilityFirstFrameStateChange（系统接口）

## offAbilityFirstFrameStateChange

```TypeScript
function offAbilityFirstFrameStateChange(observer?: AbilityFirstFrameStateObserver): void
```

取消注册监听Ability首帧绘制完成事件观察者对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function offAbilityFirstFrameStateChange(observer?: AbilityFirstFrameStateObserver): void--><!--Device-appManager-function offAbilityFirstFrameStateChange(observer?: AbilityFirstFrameStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 表示待取消的Ability首帧绘制完成事件观察者对象，不填表示取消所有监听对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class AbilityFirstFrameStateObserverCustom implements appManager.AbilityFirstFrameStateObserver {
  onAbilityFirstFrameDrawn(abilityStateData: appManager.AbilityFirstFrameStateData) {
    console.info(`abilityFirstFrame: , ${JSON.stringify(abilityStateData)}`);
  }
}

let observer = new AbilityFirstFrameStateObserverCustom();
try {
  appManager.onAbilityFirstFrameStateChange(observer);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

try {
  appManager.offAbilityFirstFrameStateChange(observer);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

