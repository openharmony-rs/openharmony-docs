# on（系统接口）

## on('abilityForegroundState')

```TypeScript
function on(type: 'abilityForegroundState', observer: AbilityForegroundStateObserver): void
```

注册Ability的启动和退出的观测器。

**起始版本：** 11

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityForegroundState' | 是 | 调用接口类型，固定填'abilityForegroundState'字符串。 |
| observer | AbilityForegroundStateObserver | 是 | Ability状态观测器，用于观测Ability的启动和退出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

**示例：**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: abilityManager.AbilityForegroundStateObserver = {
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
};
try {
  abilityManager.on('abilityForegroundState', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}

```

