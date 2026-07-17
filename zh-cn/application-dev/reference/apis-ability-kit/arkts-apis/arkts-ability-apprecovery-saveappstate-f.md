# saveAppState

## 导入模块

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## saveAppState

```TypeScript
function saveAppState(): boolean
```

保存当前App状态，可以配合[errorManager](arkts-app-ability-errormanager.md)相关接口使用。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appRecovery-function saveAppState(): boolean--><!--Device-appRecovery-function saveAppState(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 保存成功与否。true：保存成功，false：保存失败。 |

**示例：**

```TypeScript
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    appRecovery.saveAppState();
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}

```


## saveAppState

```TypeScript
function saveAppState(context?: UIAbilityContext): boolean
```

主动保存Ability的状态，这个状态将在下次恢复启动时使用。可以配合[errorManager](arkts-app-ability-errormanager.md)相关接口使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appRecovery-function saveAppState(context?: UIAbilityContext): boolean--><!--Device-appRecovery-function saveAppState(context?: UIAbilityContext): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](arkts-ability-common-uiabilitycontext-t.md) | 否 | 需要保存状态的UIAbility所对应的context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 保存成功与否。true：保存成功，false：保存失败。 |

**示例：**

```TypeScript
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    // context为UIAbility实例的context，需使用箭头函数或在回调外预先保存。
    appRecovery.saveAppState(this.context);
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}

```

