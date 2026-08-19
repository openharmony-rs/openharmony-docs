# off_abilityFirstFrameState（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## off('abilityFirstFrameState')

```TypeScript
function off(type: 'abilityFirstFrameState', observer?: AbilityFirstFrameStateObserver): void
```

取消注册监听Ability首帧绘制完成事件观察者对象。

**起始版本：** 12

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function off(type: 'abilityFirstFrameState', observer?: AbilityFirstFrameStateObserver): void--><!--Device-appManager-function off(type: 'abilityFirstFrameState', observer?: AbilityFirstFrameStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityFirstFrameState' | 是 | 调用接口类型，固定填'abilityFirstFrameState'字符串。 |
| observer | AbilityFirstFrameStateObserver | 否 | 表示待取消的Ability首帧绘制完成事件观察者对象，不填表示取消所有监听对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityFirstFrameStateObserverForAll: appManager.AbilityFirstFrameStateObserver = {
  onAbilityFirstFrameDrawn(abilityStateData: appManager.AbilityFirstFrameStateData) {
    console.info(`abilityFirstFrame: , ${JSON.stringify(abilityStateData)}`);
  }
};

try {
  appManager.on('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

try {
  appManager.off('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

