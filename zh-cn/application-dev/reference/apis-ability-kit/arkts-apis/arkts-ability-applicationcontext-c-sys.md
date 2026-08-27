# ApplicationContext

ApplicationContext作为应用上下文，继承自Context，提供了应用生命周期监听、进程管理、应用环境设置等应用级别的管控能力。

> **说明：**
> 
> 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** ApplicationContext extends Context

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(): Promise<Array<ProcessInformation>>
```

获取运行中的进程信息。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;ProcessInformation & gt; & gt; | Promise对象，返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    applicationContext.getProcessRunningInformation().then((data) => {
      console.info(`The process running information is: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error msg: ${error.message}`);
    });
  }
}
```

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

获取运行中的进程信息。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback & lt;Array & lt;ProcessInformation & gt; & gt; | 是 | 回调函数，返回有关运行进程的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    applicationContext.getProcessRunningInformation((err, data) => {
      if (err) {
        console.error(`getProcessRunningInformation failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`The process running information is: ${JSON.stringify(data)}`);
      }
    })
  }
}
```

## preloadUIExtensionAbility

```TypeScript
preloadUIExtensionAbility(want: Want): Promise<void>
```

预加载指定UIExtensionAbility实例。使用Promise异步回调。被预加载的UIExtensionAbility实例会执行到UIExtensionAbility的onCreate生命周期，然后等待被当前应用正式加载。被预加载的UIExtensionAbility实例会执行到UIExtensionAbility的onCreate生命周期，然后等待被当前应用正式加载。

**起始版本：** 12

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 预加载UIExtensionAbility的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // 构造预加载UIExtensionAbility的want参数
    let want: Want = {
      bundleName: 'com.ohos.uiextensionprovider',
      abilityName: 'UIExtensionProvider',
      moduleName: 'entry',
      parameters: {
        // 与UIExtensionAbility在module.json5中"type"字段配置一致
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    try {
      // 获取ApplicationContext实例
      let applicationContext = this.context.getApplicationContext();
      // 预加载UIExtensionAbility
      applicationContext.preloadUIExtensionAbility(want)
        .then(() => {
          // 预加载成功处理
          console.info('preloadUIExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // 预加载失败处理
          console.error('preloadUIExtensionAbility failed');
        });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`preloadUIExtensionAbility failed. code: ${code}, msg: ${message}`);
    }
  }
}
```

## registerAbilityLifecycleCallback

```TypeScript
registerAbilityLifecycleCallback(abilityLifecycleCallback: AbilityLifecycleCallback): number
```

注册监听应用内UIAbility的生命周期。使用callback异步回调。<p>**说明：**: 仅支持主线程调用。 </p>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [on](arkts-ability-applicationcontext-c.md#onabilitylifecycle)(type: 'abilityLifecycle', callback: AbilityLifecycleCallback)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityLifecycleCallback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | 是 | UIAbility生命周期变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.unregisterAbilityLifecycleCallback()]{ |

**示例**

```TypeScript
import { UIAbility, AbilityLifecycleCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    let AbilityLifecycleCallback: AbilityLifecycleCallback = {
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
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听应用内生命周期
      lifecycleId = applicationContext.registerAbilityLifecycleCallback(AbilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }
}
```

## registerEnvironmentCallback

```TypeScript
registerEnvironmentCallback(environmentCallback: EnvironmentCallback): number
```

注册对系统环境变化的监听。使用callback异步回调。<p>**说明：**: 仅支持主线程调用。 </p>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [on](arkts-ability-applicationcontext-c.md#onenvironment)(type: 'environment', callback: EnvironmentCallback)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| environmentCallback | [EnvironmentCallback](arkts-ability-app-ability-environmentcallback-environmentcallback-c.md) | 是 | 系统环境变化时触发的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回此次注册的callbackID，该ID用于在 [ApplicationContext.unregisterEnvironmentCallback]{ |

**示例**

```TypeScript
import { UIAbility, EnvironmentCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate')
    let environmentCallback: EnvironmentCallback = {
      onConfigurationUpdated(config) {
        console.info(`onConfigurationUpdated config: ${JSON.stringify(config)}`);
      },
      onMemoryLevel(level) {
        console.info(`onMemoryLevel level: ${level}`);
      }
    };
    // 1.获取applicationContext
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2.通过applicationContext注册监听系统环境变化
      callbackId = applicationContext.registerEnvironmentCallback(environmentCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }
}
```

## unregisterAbilityLifecycleCallback

```TypeScript
unregisterAbilityLifecycleCallback(callbackId: number, callback: AsyncCallback<void>): void
```

取消监听应用内UIAbility的生命周期。使用callback异步回调。<p>**说明：**: 仅支持主线程调用。 </p>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [off](arkts-ability-applicationcontext-c.md#offabilitylifecycle)(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |
| callback | AsyncCallback & lt;void & gt; | 是 | 回调方法。当取消监听应用内生命周期成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      applicationContext.unregisterAbilityLifecycleCallback(lifecycleId, (error, data) => {
        if (error) {
          console.error(`unregisterAbilityLifecycleCallback fail, err: ${JSON.stringify(error)}`);
        } else {
          console.info(`unregisterAbilityLifecycleCallback success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## unregisterAbilityLifecycleCallback

```TypeScript
unregisterAbilityLifecycleCallback(callbackId: number): Promise<void>
```

取消监听应用内UIAbility的生命周期。使用Promise异步回调。<p>**说明：**: 仅支持主线程调用。 </p>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** off(type: 'abilityLifecycle', callbackId: number): Promise&lt;void&gt;;

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) 接口注册监听应用内UIAbility的生命周期时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      applicationContext.unregisterAbilityLifecycleCallback(lifecycleId);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback<void>): void
```

取消对系统环境变化的监听。使用callback异步回调。<p>**说明：**: 仅支持主线程调用。 </p>

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [off](arkts-ability-applicationcontext-c.md#offenvironment)(type: 'environment', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) 接口注册监听系统环境变化时返回的ID。 |
| envcallback | AsyncCallback & lt;void & gt; | 是 | 回调方法。当取消对系统环境变化的监听成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.unregisterEnvironmentCallback(callbackId, (error, data) => {
        if (error) {
          console.error(`unregisterEnvironmentCallback fail, err: ${JSON.stringify(error)}`);
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

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number): Promise<void>
```

取消对系统环境变化的监听。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** off(type: 'environment', callbackId: number): Promise&lt;void&gt;;

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackId | number | 是 | 通过 [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) 接口注册监听系统环境变化时返回的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // 获取ApplicationContext实例
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.unregisterEnvironmentCallback(callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```
