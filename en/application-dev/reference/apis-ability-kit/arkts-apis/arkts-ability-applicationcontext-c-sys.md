# ApplicationContext

ApplicationContext inherits from Context and provides application-level management capabilities, such as application lifecycle listening, process management, and application environment setting.

> **NOTE:** 
> 
> The APIs of this module can be used only in the stage model.

**Inheritance/Implementation:** ApplicationContext extends [Context](arkts-ability-context-c.md)

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(): Promise<Array<ProcessInformation>>
```

Obtains information about the running processes. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ProcessInformation](arkts-ability-processinformation-i.md)&gt;&gt; | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the ApplicationContext instance.
    let applicationContext = this.context.getApplicationContext();
    applicationContext.getProcessRunningInformation().then((data) => {
      console.info(`The process running information is: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error msg: ${error.message}`);
    });
  }
}
```

```TypeScript
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the ApplicationContext instance.
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

## getProcessRunningInformation

```TypeScript
getProcessRunningInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

Obtains information about the running processes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getRunningProcessInformation](arkts-ability-applicationcontext-c.md#getrunningprocessinformation)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProcessInformation](arkts-ability-processinformation-i.md)&gt;&gt; | Yes | Callback used to return the information about the running processes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

See [getProcessRunningInformation](#getprocessrunninginformation)

## preloadUIExtensionAbility

```TypeScript
preloadUIExtensionAbility(want: Want): Promise<void>
```

Preloads a UIExtensionAbility instance. This API uses a promise to return the result.

The preloaded UIExtensionAbility instance is sent to the **onCreate** lifecycle of the UIExtensionAbility and waits to be loaded by the current application.

A UIExtensionAbility instance can be preloaded for multiple times. Each time a preloaded UIExtensionAbility instance is loaded, the next preloaded UIExtensionAbility instance is sent to the **onCreate** lifecycle of the UIExtensionAbility.

| Name| Type| Mandatory| Description|  
| -------- | -------- | -------- | -------- |  
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes| Want information of the UIExtensionAbility.|

**Since:** 12

**Required permissions:** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information of the UIExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Construct the want parameter for preloading the UIExtensionAbility.
    let want: Want = {
      bundleName: 'com.ohos.uiextensionprovider',
      abilityName: 'UIExtensionProvider',
      moduleName: 'entry',
      parameters: {
        // Consistent with the "type" field configuration of the UIExtensionAbility in module.json5.
        'ability.want.params.uiExtensionType': 'sys/commonUI'
      }
    };
    try {
      // Obtain the ApplicationContext instance.
      let applicationContext = this.context.getApplicationContext();
      // Preload the UIExtensionAbility.
      applicationContext.preloadUIExtensionAbility(want)
        .then(() => {
          // Handle the preload success.
          console.info('preloadUIExtensionAbility succeed');
        })
        .catch((err: BusinessError) => {
          // Handle the preload failure.
          console.error('preloadUIExtensionAbility failed');
        });
    } catch (err) {
      // Handle the input parameter error exception.
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

Registers a listener to monitor the ability lifecycle of the application. This API uses an asynchronous callback to return the result.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [on](arkts-ability-applicationcontext-c.md#onabilitylifecycle)(type: 'abilityLifecycle', callback: AbilityLifecycleCallback)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityLifecycleCallback | [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | Yes | Callback used to return the ID of the registered listener. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.unregisterAbilityLifecycleCallback](#unregisterabilitylifecyclecallback) |

**Examples**

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
    // 1. Obtain the applicationContext through the context attribute.
    // Obtain the ApplicationContext instance.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register a listener for the in-application lifecycle through applicationContext.
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

Register environment callback.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [on](arkts-ability-applicationcontext-c.md#onenvironment)(type: 'environment', callback: EnvironmentCallback)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| environmentCallback | [EnvironmentCallback](arkts-ability-app-ability-environmentcallback-environmentcallback-c.md) | Yes | Callback used to return the ID of the registered listener. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.unregisterEnvironmentCallback](#unregisterenvironmentcallback) |

**Examples**

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
    // 1. Obtain the applicationContext.
    // Obtain the ApplicationContext instance.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register a listener for system environment changes through the applicationContext.
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

Unregisters the listener that monitors the ability lifecycle of the application. This API uses an asynchronous callback to return the result.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [off](arkts-ability-applicationcontext-c.md#offabilitylifecycle)(type: 'abilityLifecycle', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackId | number | Yes | ID returned when the [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the ID of the registered listener. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the ApplicationContext instance.
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

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the ApplicationContext instance.
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

## unregisterAbilityLifecycleCallback

```TypeScript
unregisterAbilityLifecycleCallback(callbackId: number): Promise<void>
```

Unregisters a listener for the lifecycle of a UIAbility within the application. This API uses a promise to return the result. It can be called only on the main thread.

<p>**NOTE:**  <br>It can be called only by the main thread. </p>

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [off](arkts-ability-applicationcontext-c.md#offabilitylifecycle)(type: 'abilityLifecycle', callbackId: number): Promise&lt;void&gt;;

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackId | number | Yes | ID returned when the [ApplicationContext.registerAbilityLifecycleCallback](#registerabilitylifecyclecallback) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

See [unregisterAbilityLifecycleCallback](#unregisterabilitylifecyclecallback)

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback<void>): void
```

Unregisters the listener for system environment changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [off](arkts-ability-applicationcontext-c.md#offenvironment)(type: 'environment', callbackId: number, callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackId | number | Yes | ID returned when the [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) |
| envcallback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the ID of the registered listener. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the ApplicationContext instance.
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

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the ApplicationContext instance.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.unregisterEnvironmentCallback(callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## unregisterEnvironmentCallback

```TypeScript
unregisterEnvironmentCallback(callbackId: number): Promise<void>
```

Unregisters the listener for system environment changes. This API uses a promise to return the result. It can be called only on the main thread.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [off](arkts-ability-applicationcontext-c.md#offenvironment)(type: 'environment', callbackId: number): Promise&lt;void&gt;;

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackId | number | Yes | ID returned when the [ApplicationContext.registerEnvironmentCallback](#registerenvironmentcallback) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Examples**

See [unregisterEnvironmentCallback](#unregisterenvironmentcallback)
