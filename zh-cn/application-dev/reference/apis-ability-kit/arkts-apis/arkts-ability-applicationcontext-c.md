# ApplicationContext

ApplicationContext作为应用上下文，继承自Context，提供了应用生命周期监听、进程管理、应用环境设置等应用级别的管控能力。 > **说明：** > > 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** ApplicationContext extends Context

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class ApplicationContext--><!--Device-unnamed-declare class ApplicationContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## clearUpApplicationData

```TypeScript
clearUpApplicationData(): Promise<void>
```

清理当前应用的应用文件路径下的所有数据，同时撤销应用向用户申请的权限。使用Promise异步回调。仅支持主线程调用。 > **说明：** > > 应用文件路径详见[应用文件目录信息](../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。图中仅标识了el1~el2目录下的应用文件路径，其他文件 > 加密类型目录下的应用文件路径可以参考el1。 > > 该接口会停止应用进程，应用进程停止后，后续的所有回调都不会再触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-clearUpApplicationData(): Promise<void>--><!--Device-ApplicationContext-clearUpApplicationData(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 清理当前应用的应用文件路径下的所有数据
    applicationContext.clearUpApplicationData();
  }
}
```

## clearUpApplicationData

```TypeScript
clearUpApplicationData(callback: AsyncCallback<void>): void
```

清理当前应用的应用文件路径下的所有数据，同时撤销应用向用户申请的权限。使用callback异步回调。仅支持主线程调用。 > **说明：** > > 应用文件路径详见[应用文件目录信息](../../../file-management/app-sandbox-directory.md#应用文件目录与应用文件路径)。图中仅标识了el1~el2目录下的应用文件路径，其他文件 > 加密类型目录下的应用文件路径可以参考el1。 > > 该接口会停止应用进程，应用进程停止后，后续的所有回调都不会再触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-clearUpApplicationData(callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-clearUpApplicationData(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the result. If the application data is cleared up, &lt;code&gt;error&lt;/code&gt; is &lt;code&gt;undefined&lt;/code&gt;; otherwise, &lt;code&gt;error&lt;/code&gt; is an error object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 清理当前应用的应用文件路径下的所有数据
    applicationContext.clearUpApplicationData(error => {
      if (error) {
        console.error(`Failed to clear up application data. Code: ${error.code}, message: ${error.message}`);
      }
    });
  }
}
```

## getAllRunningInstanceKeys

```TypeScript
getAllRunningInstanceKeys(): Promise<Array<string>>
```

获取应用的所有多实例的唯一实例标识。使用Promise异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-getAllRunningInstanceKeys(): Promise<Array<string>>--><!--Device-ApplicationContext-getAllRunningInstanceKeys(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回应用的所有多实例的唯一实例标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 获取应用的所有多实例的唯一实例标识
      applicationContext.getAllRunningInstanceKeys();
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getAllRunningInstanceKeys fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## getAllWindowStages

```TypeScript
getAllWindowStages(): Promise<Array<window.WindowStage>>
```

获取应用当前进程内的所有WindowStage对象。使用Promise异步回调。仅支持主线程调用。 该接口主要用于包含多个UIAbility的应用进行多窗口管理，例如管理多个WindowStage的状态、同一应用的多个窗口间的状态或数据同步等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-getAllWindowStages(): Promise<Array<window.WindowStage>>--><!--Device-ApplicationContext-getAllWindowStages(): Promise<Array<window.WindowStage>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;window.WindowStage&gt;&gt; | Promise used to return all WindowStage objects in the current application process. |

## 示例

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 获取应用当前进程内的所有WindowStage对象
      applicationContext.getAllWindowStages().then((data: window.WindowStage[]) => {
        let windowStage: window.WindowStage[] = data;
        console.info(`WindowStages size ${windowStage.length}`);
      }).catch((error: BusinessError) => {
        console.error(`getAllWindowStages error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getAllWindowStages fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## getCurrentAppCloneIndex

```TypeScript
getCurrentAppCloneIndex(): int
```

获取当前应用的分身索引。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-getCurrentAppCloneIndex(): int--><!--Device-ApplicationContext-getCurrentAppCloneIndex(): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前应用的分身索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000071](../errorcode-ability.md#16000071-不支持应用分身模式) | The MultiAppMode is not App_CLONE. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 获取当前应用的分身索引
      let appCloneIndex = applicationContext.getCurrentAppCloneIndex();
    } catch (error) {
      console.error(`Failed to get current app clone index. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

## getCurrentInstanceKey

```TypeScript
getCurrentInstanceKey(): string
```

获取当前应用多实例的唯一实例标识。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-getCurrentInstanceKey(): string--><!--Device-ApplicationContext-getCurrentInstanceKey(): string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回当前应用多实例的唯一实例标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000078](../errorcode-ability.md#16000078-不支持应用多实例) | The multi-instance is not supported. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    let currentInstanceKey = '';
    try {
      // 获取当前应用多实例的唯一实例标识
      currentInstanceKey = applicationContext.getCurrentInstanceKey();
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getCurrentInstanceKey fail, code: ${code}, msg: ${message}`);
    }
    console.info(`currentInstanceKey: ${currentInstanceKey}`);
  }
}
```

## getRunningProcessInformation

```TypeScript
getRunningProcessInformation(): Promise<Array<ProcessInformation>>
```

获取运行中的进程信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-getRunningProcessInformation(): Promise<Array<ProcessInformation>>--><!--Device-ApplicationContext-getRunningProcessInformation(): Promise<Array<ProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ProcessInformation&gt;&gt; | Promise对象，返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 获取运行中的进程信息
    applicationContext.getRunningProcessInformation().then((data) => {
      console.info(`The process running information is: ${JSON.stringify(data)}`);
    }).catch((error: Error): void => {
      let err = error as BusinessError;
      console.error(`error: code: ${err.code} message: ${err.message}`);
    });
  }
}
```

## getRunningProcessInformation

```TypeScript
getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

获取运行中的进程信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void--><!--Device-ApplicationContext-getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;ProcessInformation&gt;&gt; | 是 | 回调函数，返回有关运行进程的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 获取运行中的进程信息
    applicationContext.getRunningProcessInformation((err, data) => {
      if (err) {
        console.error(`Failed to get running process information. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.info(`The process running information is: ${JSON.stringify(data)}`);
      }
    });
  }
}
```

## killAllProcesses

```TypeScript
killAllProcesses(): Promise<void>
```

终止应用的所有进程，进程退出时不会正常执行完整的应用生命周期流程。使用Promise异步回调。仅支持主线程调用。 > **说明：** > > 该接口用于应用异常场景中强制退出应用。如需正常退出应用，可以使用[terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateSelf)接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-killAllProcesses(): Promise<void>--><!--Device-ApplicationContext-killAllProcesses(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 终止应用的所有进程
    applicationContext.killAllProcesses();
  }
}
```

## killAllProcesses

```TypeScript
killAllProcesses(clearPageStack: boolean): Promise<void>
```

终止应用的所有进程，进程退出时不会正常执行完整的应用生命周期流程。使用Promise异步回调。仅支持主线程调用。 > **说明：** > > 该接口用于应用异常场景中强制退出应用。如需正常退出应用，可以使用[terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateSelf)接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-killAllProcesses(clearPageStack: boolean): Promise<void>--><!--Device-ApplicationContext-killAllProcesses(clearPageStack: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearPageStack | boolean | 是 | 表示是否清除页面堆栈。true表示清除，false表示不清除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

let isClearPageStack = false;

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 终止应用的所有进程,并清除页面堆栈
    applicationContext.killAllProcesses(isClearPageStack);
  }
}
```

## killAllProcesses

```TypeScript
killAllProcesses(callback: AsyncCallback<void>): void
```

终止应用的所有进程，进程退出时不会正常执行完整的应用生命周期流程。使用callback异步回调。仅支持主线程调用。 > **说明：** > > 该接口用于应用异常场景中强制退出应用。如需正常退出应用，可以使用[terminateSelf()](arkts-ability-uiabilitycontext-c.md#terminateSelf)接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-killAllProcesses(callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-killAllProcesses(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当终止应用所在的进程成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 终止应用的所有进程
    applicationContext.killAllProcesses(error => {
      if (error) {
        console.error(`Failed to kill all processes. Code: ${error.code}, message: ${error.message}`);
      }
    });
  }
}
```

## offAbilityLifecycle

```TypeScript
offAbilityLifecycle(callbackId: int, callback: AsyncCallback<void>): void
```

取消监听应用内UIAbility的生命周期。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offAbilityLifecycle(callbackId: int, callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-offAbilityLifecycle(callbackId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | int | 是 | 通过 [ApplicationContext.on('abilityLifecycle')](#on_abilityLifecycle) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消监听应用内生命周期成功，err为undefined，否则为错误对象。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let lifecycleId: int;

class AbilityLifecycleCallbackCustom extends AbilityLifecycleCallback {
  onAbilityCreate(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
  }

  onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
  }

  onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
  }

  onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
  }

  onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
  }

  onAbilityDestroy(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
  }

  onAbilityForeground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
  }

  onAbilityBackground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
  }

  onAbilityContinue(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');

    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听应用内生命周期
      let abilityLifecycleCallback = new AbilityLifecycleCallbackCustom();
      lifecycleId = applicationContext.onAbilityLifecycle(abilityLifecycleCallback);
      applicationContext.offAbilityLifecycle(lifecycleId, (err: BusinessError<void> | null) => {
        if (err?.code) {
          console.error(`unregisterAbilityLifecycleCallback fail, err: ${JSON.stringify(err)}`);
          return;
        }
        console.info(`unregisterAbilityLifecycleCallback success}`);
      });
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## offAbilityLifecycle

```TypeScript
offAbilityLifecycle(callbackId: int): Promise<void>
```

取消监听应用内UIAbility的生命周期。使用Promise异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offAbilityLifecycle(callbackId: int): Promise<void>--><!--Device-ApplicationContext-offAbilityLifecycle(callbackId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | int | 是 | 通过 [ApplicationContext.on('abilityLifecycle')](#on_abilityLifecycle) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let lifecycleId: int;

class AbilityLifecycleCallbackCustom extends AbilityLifecycleCallback {
  onAbilityCreate(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
  }

  onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
  }

  onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
  }

  onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
  }

  onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
  }

  onAbilityDestroy(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
  }

  onAbilityForeground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
  }

  onAbilityBackground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
  }

  onAbilityContinue(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');

    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听应用内生命周期
      let abilityLifecycleCallback = new AbilityLifecycleCallbackCustom();
      lifecycleId = applicationContext.onAbilityLifecycle(abilityLifecycleCallback);
      applicationContext.offAbilityLifecycle(lifecycleId, (err: BusinessError<void> | null) => {
        if (err?.code) {
          console.error(`unregisterAbilityLifecycleCallback fail, err: ${JSON.stringify(err)}`);
          return;
        }
        console.info(`unregisterAbilityLifecycleCallback success}`);
      });
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## offApplicationStateChange

```TypeScript
offApplicationStateChange(callback?: ApplicationStateChangeCallback): void
```

取消对应用前后台状态变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offApplicationStateChange(callback?: ApplicationStateChangeCallback): void--><!--Device-ApplicationContext-offApplicationStateChange(callback?: ApplicationStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | 否 | 回调函数。取值可以为使用 [ApplicationContext.onApplicationStateChange](#on_applicationStateChange)方法定义的callback回 调，也可以为空。 - 如果传入已定义的回调，则取消该监听。 - 如果未传入参数，则取消当前应用对所有前后台切换事件的监听。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ApplicationStateChangeCallbackCustom implements ApplicationStateChangeCallback {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  }

  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
}

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // 1.获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    let applicationStateChangeCallbackCb = new ApplicationStateChangeCallbackCustom();
    try {
      // 2.通过applicationContext注册应用前后台状态监听
      applicationContext.offApplicationStateChange(applicationStateChangeCallbackCb);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## offEnvironment

```TypeScript
offEnvironment(callbackId: int, callback: AsyncCallback<void>): void
```

取消对系统环境变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offEnvironment(callbackId: int, callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-offEnvironment(callbackId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | int | 是 | 通过[ApplicationContext.onEnvironment](#on_environment)接口注册监听系统环 境变化时返回的ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消对系统环境变化的监听成功，err为undefined，否则为错误对象。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, EnvironmentCallback, Configuration, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: int;

class EnvironmentCallbackCustom implements EnvironmentCallback {
  onConfigurationUpdated(config: Configuration) {
    console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
  }

  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`onMemoryLevel level: ${level}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate')
    // 1.获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    let environmentCallbackCb = new EnvironmentCallbackCustom();
    try {
      // 2.通过applicationContext注册监听系统环境变化
      callbackId = applicationContext.onEnvironment(environmentCallbackCb);
      applicationContext.offEnvironment(callbackId, (err: BusinessError<void> | null) => {
        if (err?.code) {
          console.error(`unregisterEnvironmentCallback fail, err: ${JSON.stringify(err)}`);
          return;
        }
        console.info(`unregisterEnvironmentCallback success}`);
      });
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }
}
```

## offEnvironment

```TypeScript
offEnvironment(callbackId: int): Promise<void>
```

取消对系统环境变化的监听。使用Promise异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offEnvironment(callbackId: int): Promise<void>--><!--Device-ApplicationContext-offEnvironment(callbackId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | int | 是 | 通过[ApplicationContext.onEnvironment](#on_environment)接口注册监听系统环境 变化时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, EnvironmentCallback, Configuration, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: int;

class EnvironmentCallbackCustom implements EnvironmentCallback {
  onConfigurationUpdated(config: Configuration) {
    console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
  }

  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`onMemoryLevel level: ${level}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate')
    // 1.获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    let environmentCallbackCb = new EnvironmentCallbackCustom();
    try {
      // 2.通过applicationContext注册监听系统环境变化
      callbackId = applicationContext.onEnvironment(environmentCallbackCb);
      applicationContext.offEnvironment(callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }
}
```

## offInteropAbilityLifecycle

```TypeScript
offInteropAbilityLifecycle(callback?: InteropAbilityLifecycleCallback): void
```

取消应用内不同ArkTS环境下UIAbility生命周期的监听。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-offInteropAbilityLifecycle(callback?: InteropAbilityLifecycleCallback): void--><!--Device-ApplicationContext-offInteropAbilityLifecycle(callback?: InteropAbilityLifecycleCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | InteropAbilityLifecycleCallback | 否 | 不同ArkTS环境下UIAbility生命周期变化时触发的回调方法。 |

## offSystemConfigurationUpdated

```TypeScript
offSystemConfigurationUpdated(callback?: systemConfiguration.UpdatedCallback): void
```

取消监听系统环境[Configuration](arkts-ability-app-ability-configuration-configuration-i.md#Configuration)的变化。仅支持主线程调用。 &lt;p&gt;**NOTE：**: &lt;br&gt;It can be called only by the main thread. &lt;/p&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-offSystemConfigurationUpdated(callback?: systemConfiguration.UpdatedCallback): void--><!--Device-ApplicationContext-offSystemConfigurationUpdated(callback?: systemConfiguration.UpdatedCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | systemConfiguration.UpdatedCallback | 否 | 回调函数。取值可以为使用 [ApplicationContext.onSystemConfigurationUpdated](#onSystemConfigurationUpdated) 方法注册的callback回调，也可以为空。&lt;br/&gt;-&nbsp;如果传入已定义的回调，则取消该监听。 &lt;br/&gt;-&nbsp;如果未传入参数，则取消所有已注册的监听。 |

## 示例

```TypeScript
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let callBack: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
        console.info(`system configuration updated colormode:` + colorMode);
      },
      onFontSizeScaleUpdated(fontSizeScale: number) {
        console.info(`system configuration updated ability:` + fontSizeScale);
      },
      onFontWeightScaleUpdated(fontWeightScale: number) {
        console.info(`system configuration updated ability:` + fontWeightScale);
      },
      onMCCUpdated(mcc: string) {
        console.info(`system configuration updated ability:` + mcc);
      },
      onMNCUpdated(mnc: string) {
        console.info(`system configuration updated ability:` + mnc);
      },
      onLanguageUpdated(language: string) {
        console.info(`system configuration updated ability:` + language);
      },
      onFontIdUpdated(fontId: string) {
        console.info(`system configuration updated ability:` + fontId);
      },
      onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
        console.info(`system configuration updated ability:` + hasPointerDevice);
      },
      onLocaleUpdated(locale: string) {
        console.info(`system configuration updated ability:` + locale);
      }
    }
    // 1.通过context属性获取applicationContext
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext取消监听
      applicationContext.offSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`offSystemConfigurationUpdated finish`);
  }
}
```

## off_abilityLifecycle

```TypeScript
off(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback<void>): void
```

取消监听应用内UIAbility的生命周期。使用callback异步回调。仅支持主线程调用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-off(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-off(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | 是 | 此类型表示应用内UIAbility的生命周期，固定为'abilityLifecycle'。 |
| callbackId | number | 是 | 通过 [ApplicationContext.on('abilityLifecycle')](#on_abilityLifecycle) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消监听应用内生命周期成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // 取消监听应用内UIAbility生命周期
      applicationContext.off('abilityLifecycle', lifecycleId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister abilityLifecycle callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterAbilityLifecycleCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off_abilityLifecycle

```TypeScript
off(type: 'abilityLifecycle', callbackId: number): Promise<void>
```

取消监听应用内UIAbility的生命周期。使用Promise异步回调。仅支持主线程调用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-off(type: 'abilityLifecycle', callbackId: number): Promise<void>--><!--Device-ApplicationContext-off(type: 'abilityLifecycle', callbackId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | 是 | 此类型表示应用内UIAbility的生命周期，固定为'abilityLifecycle'。 |
| callbackId | number | 是 | 通过 [ApplicationContext.on('abilityLifecycle')](#on_abilityLifecycle) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // 取消监听应用内UIAbility生命周期
      applicationContext.off('abilityLifecycle', lifecycleId);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off_applicationStateChange

```TypeScript
off(type: 'applicationStateChange', callback?: ApplicationStateChangeCallback): void
```

取消对当前应用进程状态变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-off(type: 'applicationStateChange', callback?: ApplicationStateChangeCallback): void--><!--Device-ApplicationContext-off(type: 'applicationStateChange', callback?: ApplicationStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'applicationStateChange' | 是 | 此类型表示当前应用进程状态变化，固定为'applicationStateChange'。 |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | 否 | 回调函数。取值可以为使用 [ApplicationContext.on('applicationStateChange')](#on_abilityLifecycle) 方法定义的callback回调，也可以为空。&lt;br/&gt;-?如果传入已定义的回调，则取消该监听。 &lt;br/&gt;-?如果未传入参数，则取消所有已注册的该类型事件的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

假定已使用[ApplicationContext.on('applicationStateChange')](#onApplicationStateChange)方法注册名为applicationStateChangeCallback回调，下面示例展示如何取消对应的事件监听。

```TypeScript
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateChangeCallback: ApplicationStateChangeCallback = {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  },
  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
};

export default class MyAbility extends UIAbility {
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 本例中的callback参数取值为ApplicationStateChangeCallback，需要替换为实际值。
      // 如果callback字段不传入参数，则取消所有已注册的该类型事件的监听。
      applicationContext.off('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off_environment

```TypeScript
off(type: 'environment', callbackId: number, callback: AsyncCallback<void>): void
```

取消对系统环境变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-off(type: 'environment', callbackId: number, callback: AsyncCallback<void>): void--><!--Device-ApplicationContext-off(type: 'environment', callbackId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'environment' | 是 | 此类型表示系统环境变化，如系统深浅色发生变化，固定为'environment'。 |
| callbackId | number | 是 | 通过 [ApplicationContext.on('environment')](#on_abilityLifecycle) 接口注册监听系统环境变化时返回的ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调方法。当取消对系统环境变化的监听成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2 .Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 取消对系统环境变化的监听
      applicationContext.off('environment', callbackId, (error, data) => {
        if (error) {
          console.error(`Failed to unregister environment callback. Code: ${error.code}, message: ${error.message}`);
        } else {
          console.info(`unregisterEnvironmentCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## off_environment

```TypeScript
off(type: 'environment', callbackId: number): Promise<void>
```

取消对系统环境变化的监听。使用Promise异步回调。仅支持主线程调用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-off(type: 'environment', callbackId: number): Promise<void>--><!--Device-ApplicationContext-off(type: 'environment', callbackId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'environment' | 是 | 此类型表示系统环境变化，如系统深浅色发生变化，固定为'environment'。 |
| callbackId | number | 是 | 通过 [ApplicationContext.on('environment')](#on_abilityLifecycle) 接口注册监听系统环境变化时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2 .Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 取消对系统环境变化的监听
      applicationContext.off('environment', callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## onAbilityLifecycle

```TypeScript
onAbilityLifecycle(callback: AbilityLifecycleCallback): int
```

注册监听应用内UIAbility的生命周期。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-onAbilityLifecycle(callback: AbilityLifecycleCallback): int--><!--Device-ApplicationContext-onAbilityLifecycle(callback: AbilityLifecycleCallback): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | 是 | UIAbility生命周期变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回此次注册的callbackID（每次注册该ID会自增+1，当超过监听上限数量2^63-1时，返回-1），该ID用于在ApplicationContext.offAbilityLifecycle方法中取消注册对应的callback。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let lifecycleId: int;

class AbilityLifecycleCallbackCustom extends AbilityLifecycleCallback {
  onAbilityCreate(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
  }

  onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
  }

  onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
  }

  onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
  }

  onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
    console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
  }

  onAbilityDestroy(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
  }

  onAbilityForeground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
  }

  onAbilityBackground(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
  }

  onAbilityContinue(ability: UIAbility) {
    console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');

    // 1.通过context属性获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听应用内生命周期
      let abilityLifecycleCallback = new AbilityLifecycleCallbackCustom();
      lifecycleId = applicationContext.onAbilityLifecycle(abilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## onApplicationStateChange

```TypeScript
onApplicationStateChange(callback: ApplicationStateChangeCallback): void
```

注册对当前应用前后台状态变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-onApplicationStateChange(callback: ApplicationStateChangeCallback): void--><!--Device-ApplicationContext-onApplicationStateChange(callback: ApplicationStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | 是 | 应用前后台切换时触发的回调方法。 |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ApplicationStateChangeCallbackCustom implements ApplicationStateChangeCallback {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  }

  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
}

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // 1.获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    let applicationStateChangeCallbackCb = new ApplicationStateChangeCallbackCustom();
    try {
      // 2.通过applicationContext注册应用前后台状态监听
      applicationContext.onApplicationStateChange(applicationStateChangeCallbackCb);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info('Register applicationStateChangeCallback');
  }
}
```

## onEnvironment

```TypeScript
onEnvironment(callback: EnvironmentCallback): int
```

注册对系统环境变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-onEnvironment(callback: EnvironmentCallback): int--><!--Device-ApplicationContext-onEnvironment(callback: EnvironmentCallback): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [EnvironmentCallback](../../apis-na/arkts-apis/arkts-na-app-ability-environmentcallback-environmentcallback-i.md) | 是 | 系统环境变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回此次注册的callbackID（每次注册该ID会自增+1，当超过监听上限数量2^63-1时，返回-1），该ID用于在 [ApplicationContext.offEnvironment]{ |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIAbility, EnvironmentCallback, Configuration, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: int;

class EnvironmentCallbackCustom implements EnvironmentCallback {
  onConfigurationUpdated(config: Configuration) {
    console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
  }

  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`onMemoryLevel level: ${level}`);
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate')
    // 1.获取applicationContext
    let applicationContext = this.context.getApplicationContext();
    let environmentCallbackCb = new EnvironmentCallbackCustom();
    try {
      // 2.通过applicationContext注册监听系统环境变化
      callbackId = applicationContext.onEnvironment(environmentCallbackCb);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }
}
```

## onInteropAbilityLifecycle

```TypeScript
onInteropAbilityLifecycle(callback: InteropAbilityLifecycleCallback): void
```

注册监听应用内不同ArkTS环境下的UIAbility生命周期。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-onInteropAbilityLifecycle(callback: InteropAbilityLifecycleCallback): void--><!--Device-ApplicationContext-onInteropAbilityLifecycle(callback: InteropAbilityLifecycleCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | InteropAbilityLifecycleCallback | 是 | 不同ArkTS环境下UIAbility生命周期变化时触发的回调方法。 |

## onSystemConfigurationUpdated

```TypeScript
onSystemConfigurationUpdated(callback: systemConfiguration.UpdatedCallback): void
```

注册监听系统环境[Configuration](arkts-ability-app-ability-configuration-configuration-i.md#Configuration)的变化。使用callback异步回调。仅支持主线程调用。 > **说明：** > > 应用自定义的设置不影响回调函数的触发。例如：应用自定义设置了深浅色模式，当系统深浅色模式变化后，注册的回调函数依然会触发。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-onSystemConfigurationUpdated(callback: systemConfiguration.UpdatedCallback): void--><!--Device-ApplicationContext-onSystemConfigurationUpdated(callback: systemConfiguration.UpdatedCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | systemConfiguration.UpdatedCallback | 是 | 系统环境变化时触发的回调方法。 |

## 示例

```TypeScript
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    let callBack: systemConfiguration.UpdatedCallback = {
      onColorModeUpdated(colorMode: ConfigurationConstant.ColorMode) {
        console.info(`system configuration updated colormode:` + colorMode);
      },
      onFontSizeScaleUpdated(fontSizeScale: number) {
        console.info(`system configuration updated ability:` + fontSizeScale);
      },
      onFontWeightScaleUpdated(fontWeightScale: number) {
        console.info(`system configuration updated ability:` + fontWeightScale);
      },
      onLanguageUpdated(language: string) {
        console.info(`system configuration updated ability:` + language);
      },
      onFontIdUpdated(fontId: string) {
        console.info(`system configuration updated ability:` + fontId);
      },
      onMCCUpdated(mcc: string) {
        console.info(`system configuration updated ability:` + mcc);
      },
      onMNCUpdated(mnc: string) {
        console.info(`system configuration updated ability:` + mnc);
      },
      onHasPointerDeviceUpdated(hasPointerDevice: boolean) {
        console.info(`system configuration updated ability:` + hasPointerDevice);
      },
      onLocaleUpdated(locale: string) {
        console.info(`system configuration updated ability:` + locale);
      }
    }
    // 1.通过context属性获取applicationContext
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听
      applicationContext.onSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }
}
```

## on_abilityLifecycle

```TypeScript
on(type: 'abilityLifecycle', callback: AbilityLifecycleCallback): number
```

注册监听应用内UIAbility的生命周期。使用callback异步回调。仅支持主线程调用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-on(type: 'abilityLifecycle', callback: AbilityLifecycleCallback): number--><!--Device-ApplicationContext-on(type: 'abilityLifecycle', callback: AbilityLifecycleCallback): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityLifecycle' | 是 | 此类型表示应用内UIAbility的生命周期，固定为'abilityLifecycle'。 |
| callback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | 是 | UIAbility生命周期变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.off('abilityLifecycle')]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let abilityLifecycleCallback: AbilityLifecycleCallback = {
      onAbilityCreate(ability) {
        console.info(`AbilityLifecycleCallback onAbilityCreate ability: ${ability}`);
      },
      onWindowStageCreate(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageCreate ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageCreate windowStage: ${windowStage}`);
      },
      onWindowStageActive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageActive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageActive windowStage: ${windowStage}`);
      },
      onWindowStageInactive(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageInactive ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageInactive windowStage: ${windowStage}`);
      },
      onWindowStageDestroy(ability, windowStage) {
        console.info(`AbilityLifecycleCallback onWindowStageDestroy ability: ${ability}`);
        console.info(`AbilityLifecycleCallback onWindowStageDestroy windowStage: ${windowStage}`);
      },
      onAbilityDestroy(ability) {
        console.info(`AbilityLifecycleCallback onAbilityDestroy ability: ${ability}`);
      },
      onAbilityForeground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityForeground ability: ${ability}`);
      },
      onAbilityBackground(ability) {
        console.info(`AbilityLifecycleCallback onAbilityBackground ability: ${ability}`);
      },
      onAbilityContinue(ability) {
        console.info(`AbilityLifecycleCallback onAbilityContinue ability: ${ability}`);
      }
    }
    // 1.通过context属性获取applicationContext
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听应用内生命周期
      lifecycleId = applicationContext.on('abilityLifecycle', abilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## on_applicationStateChange

```TypeScript
on(type: 'applicationStateChange', callback: ApplicationStateChangeCallback): void
```

注册对当前应用进程状态变化的监听。使用callback异步回调。仅支持主线程调用。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-on(type: 'applicationStateChange', callback: ApplicationStateChangeCallback): void--><!--Device-ApplicationContext-on(type: 'applicationStateChange', callback: ApplicationStateChangeCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'applicationStateChange' | 是 | 此类型表示当前应用进程状态变化，固定为'applicationStateChange'。 |
| callback | [ApplicationStateChangeCallback](arkts-ability-app-ability-applicationstatechangecallback-applicationstatechangecallback-c.md) | 是 | 当前应用进程状态切换时触发的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let applicationStateChangeCallback: ApplicationStateChangeCallback = {
      onApplicationForeground() {
        console.info('applicationStateChangeCallback onApplicationForeground');
      },
      onApplicationBackground() {
        console.info('applicationStateChangeCallback onApplicationBackground');
      }
    }

    // 1.获取applicationContext
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册当前应用进程状态监听
      applicationContext.on('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info('Register applicationStateChangeCallback');
  }
}
```

## on_environment

```TypeScript
on(type: 'environment', callback: EnvironmentCallback): number
```

注册对系统环境变化的监听。使用callback异步回调。仅支持主线程调用。 > **说明：** > > - 使用[onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onConfigurationUpdate)也可以实现对系统环境变量的监听。相较 > 于Ability的[onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onConfigurationUpdate)接口，当前接口的使用场景更 > 加灵活，不仅可以在应用组件中使用，还可以在页面中使用，但是支持订阅的环境变量与Ability的 > [onConfigurationUpdate](arkts-ability-app-ability-ability-ability-c.md#onConfigurationUpdate)接口存在差异，如不支持订阅direction > 、screenDensity、displayId，详见[Configuration](arkts-ability-app-ability-configuration-configuration-i.md#Configuration)中各个环境变量的说明。 > > - 当前接口在实际触发时存在一定限制。例如如果开发者通过[setLanguage](#setLanguage)接口设置应用的语言，即便系统语 > 言发生变化，系统也不再触发当前接口的[callback](../../apis-na/arkts-apis/arkts-na-app-ability-environmentcallback-environmentcallback-i.md#EnvironmentCallback)回调。详见 > [使用场景](../../../application-models/subscribe-system-environment-variable-changes.md#使用场景)。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-on(type: 'environment', callback: EnvironmentCallback): number--><!--Device-ApplicationContext-on(type: 'environment', callback: EnvironmentCallback): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'environment' | 是 | 此类型表示系统环境变化，如系统深浅色发生变化，固定为'environment'。 |
| callback | [EnvironmentCallback](../../apis-na/arkts-apis/arkts-na-app-ability-environmentcallback-environmentcallback-i.md) | 是 | 系统环境变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.off('environment')]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2 .Incorrect parameter types. |

## 示例

```TypeScript
import { UIAbility, EnvironmentCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let environmentCallback: EnvironmentCallback = {
      onConfigurationUpdated(config) {
        console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
      },
      onMemoryLevel(level) {
        console.info(`onMemoryLevel level: ${level}`);
      }
    };
    // 1.获取applicationContext
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听系统环境变化
      callbackId = applicationContext.on('environment', environmentCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }
}
```

## restartApp

```TypeScript
restartApp(want: Want): void
```

应用重启并拉起自身指定UIAbility。仅支持主线程调用，且待重启的应用需要处于获焦状态。 > **说明：** > > 通过该接口重启应用时，不会触发应用中Ability的onDestroy生命周期回调。 > > 在原子化服务调用本接口成功后的3秒内，再次调用本接口、 > [restartSelfAtomicService()](arkts-ability-abilitymanager-restartselfatomicservice-f.md#restartSelfAtomicService) > 或[UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartApp)接口中的任一接口，系统将返回错误码16000064。 > > 在应用调用本接口成功后的3秒内，若再次调用本接口或[UIAbilityContext.restartApp()](arkts-ability-uiabilitycontext-c.md#restartApp)接口中的任 > 一接口，系统将返回错误码16000064。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-restartApp(want: Want): void--><!--Device-ApplicationContext-restartApp(want: Want): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | Want information about the UIAbility to start. No verification is performed on the bundle name passed in. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000064](../errorcode-ability.md#16000064-重启应用频繁) | Restart too frequently. Try again at least 3s later. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000063](../errorcode-ability.md#16000063-重启应用指定组件无效) | The target to restart does not belong to the current application or is not a UIAbility. |

## 示例

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { common, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'restartApp';
  private context = this.getUIContext().getHostContext()?.getApplicationContext() as common.ApplicationContext;

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility'
          };
          if (this.context) {
            try {
              // 重启应用并拉起指定UIAbility
              this.context.restartApp(want);
            } catch (err) {
              hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
            }
          } else {
            hilog.error(0x0000, 'testTag', '%{public}s', 'AppContext is null');
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

设置应用的深浅色模式。仅支持主线程调用。 > **说明：** > > 调用该接口前，需要确保窗口已完成创建、且UIAbility对应的页面已完成加载，即在 > [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onWindowStageCreate)生命周期中通过 > [loadContent](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法加载页面之后调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-setColorMode(colorMode: ConfigurationConstant.ColorMode): void--><!--Device-ApplicationContext-setColorMode(colorMode: ConfigurationConstant.ColorMode): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorMode | ConfigurationConstant.ColorMode | 是 | 深浅色模式，包括：深色模式、浅色模式、未设置颜色模式（默认）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility, ConfigurationConstant } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err?.code) {
        console.error(`Failed to load the content. Code: ${err?.code}, message: ${err?.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
      // 获取应用上下文
      let applicationContext = this.context.getApplicationContext();
      // 设置应用为深色模式
      applicationContext.setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
    });
  }
}
```

## setFont

```TypeScript
setFont(font: string): void
```

设置应用的字体类型。仅支持主线程调用。 > **说明：** > > 调用该接口前，需要确保窗口已完成创建、且UIAbility对应的页面已完成加载，即在 > [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onWindowStageCreate)生命周期中通过 > [loadContent](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法加载页面之后调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-setFont(font: string): void--><!--Device-ApplicationContext-setFont(font: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | string | 是 | 设置字体类型，字体可以通过 [UIContext.registerFont](../../../reference/apis-arkui/arkts-apis-uicontext-font.md#registerfont)方法进行注册使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  aboutToAppear() {
    this.getUIContext().getFont().registerFont({
      familyName: 'fontName',
      familySrc: $rawfile('font/medium.ttf')  // 'font/medium.ttf'仅作为示例，实际使用时请替换为真实的字体资源文件。
    });

    // 设置应用使用注册的自定义字体
    this.context.getApplicationContext().setFont('fontName');
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { common } from '@kit.AbilityKit';
import { Entry, Text, Column, Row, Component, State } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

  aboutToAppear() {
    this.getUIContext().getFont().registerFont({
      familyName: 'fontName',
      familySrc: 'font/medium.ttf'
    })

    this.context.getApplicationContext().setFont("fontName");
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## setFontSizeScale

```TypeScript
setFontSizeScale(fontSizeScale: double): void
```

设置应用字体大小缩放比例。仅支持主线程调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-setFontSizeScale(fontSizeScale: double): void--><!--Device-ApplicationContext-setFontSizeScale(fontSizeScale: double): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontSizeScale | double | 是 | 表示字体缩放比例，取值为非负数。当应用字体 [跟随系统](../../../quick-start/app-configuration-file.md#configuration标签)且该字段取值超过 [fontSizeMaxScale](../../../quick-start/app-configuration-file.md#configuration标签)取值时，实际生效值为 [fontSizeMaxScale](../../../quick-start/app-configuration-file.md#configuration标签)取值。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err?.code) {
        return;
      }
      // 获取应用上下文
      let applicationContext = this.context.getApplicationContext();
      // 设置应用字体大小缩放比例
      applicationContext.setFontSizeScale(2);
    });
  }
}
```

## setLanguage

```TypeScript
setLanguage(language: string): void
```

设置应用的语言。仅支持主线程调用。 > **说明：** > > 调用该接口前，需要确保窗口已完成创建、且UIAbility对应的页面已完成加载，即在 > [onWindowStageCreate()](arkts-ability-app-ability-uiability-uiability-c.md#onWindowStageCreate)生命周期中通过 > [loadContent](../../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9)方法加载页面之后调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationContext-setLanguage(language: string): void--><!--Device-ApplicationContext-setLanguage(language: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| language | string | 是 | 设置语言，当前支持的语言列表可以通过 [getSystemLanguages()](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-system-c.md#getSystemLanguages)获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err?.code) {
        console.error(`Failed to load the content. Code: ${err?.code}, message: ${err?.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    // 设置应用语言为中文
    applicationContext.setLanguage('zh-cn');
  }
}
```

## setSupportedProcessCache

```TypeScript
setSupportedProcessCache(isSupported : boolean): void
```

设置当前应用进程是否支持进程资源的缓存，便于应用再次启动时复用缓存的进程资源。仅支持主线程调用。 该接口仅对单个进程实例生效，不同进程实例互不影响。应用进程实例销毁后，已设置的状态不保留，需要重新设置。 > **说明：** > > - 该接口仅表示应用自身是否为缓存后快速启动做好了准备，还需综合其他条件来判断最终是否为应用启用快速启动。 > > - 为了确保该接口在进程退出前生效，调用时机应尽量提前。建议在[AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md#AbilityStage)的`onCreate() > `中调用该接口。 > > - 在同一进程多次调用该接口时，会以最后一次调用的结果为准。当存在多个AbilityStage时，为了确保结果符合预期，需要在各个AbilityStage中分别调用该接口并配置相同的取值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ApplicationContext-setSupportedProcessCache(isSupported : boolean): void--><!--Device-ApplicationContext-setSupportedProcessCache(isSupported : boolean): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSupported | boolean | 是 | Whether process cache is supported. The value &lt;code&gt;true&lt;/code&gt; means that process cache is supported, and &lt;code&gt;false&lt;/code&gt; means the opposite. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

## 示例

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 设置当前应用进程支持进程资源的缓存
      applicationContext.setSupportedProcessCache(true);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`setSupportedProcessCache fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

