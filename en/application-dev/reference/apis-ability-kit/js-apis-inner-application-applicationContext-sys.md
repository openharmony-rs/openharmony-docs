# ApplicationContext (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T11:41:44.872Z pushedAt=2026-09-05T10:47:30.689Z -->

The ApplicationContext module, inherited from [Context](js-apis-inner-application-context.md), provides the application-level context capabilities for developers, including registering and unregistering listeners for the lifecycle of in-application components.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [ApplicationContext](js-apis-inner-application-applicationContext.md).
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Usage

Before using the capabilities of ApplicationContext, you need to obtain an instance through context.

## ApplicationContext.preloadUIExtensionAbility<sup>12+</sup>

preloadUIExtensionAbility(want: Want): Promise\<void\>

Preloads a specified UIExtensionAbility instance. This API uses a promise to return the result.

The preloaded UIExtensionAbility instance runs to the onCreate lifecycle of UIExtensionAbility and then waits to be formally loaded by the current application.

Multiple UIExtensionAbility instances can be preloaded. Each time a formal load is performed, a preloaded UIExtensionAbility instance continues from onCreate to complete the UIExtensionAbility lifecycle.

**System API**: This is a system API.

**Required permissions**: ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)  | Yes | Want information of the UIExtensionAbility to preload. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------------------------------- |
| 201     | The application does not have permission to call the interface. |
| 202     | The application is not system-app, can not use system-api. |
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
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
## ApplicationContext.registerAbilityLifecycleCallback<sup>(deprecated)</sup>

registerAbilityLifecycleCallback(abilityLifecycleCallback: AbilityLifecycleCallback): number

Registers a listener for the in-application UIAbility lifecycle. This API uses an asynchronous callback. Main thread only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. It is recommended to use [ApplicationContext.on('abilityLifecycle')](js-apis-inner-application-applicationContext.md#applicationcontextonabilitylifecycle) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name                     | Type     | Mandatory | Description                           |
| ------------------------ | -------- | --------- | ------------------------------------- |
| abilityLifecycleCallback | [AbilityLifecycleCallback](js-apis-app-ability-abilityLifecycleCallback.md) | Yes   | Callback invoked when the UIAbility lifecycle changes. |

**Return value**

| Type   | Description                                                         |
| ------ | ------------------------------------------------------------ |
| number | ID of the registered callback, which is used to unregister the corresponding callback in [ApplicationContext.unregisterAbilityLifecycleCallback](#applicationcontextunregisterabilitylifecyclecallbackdeprecated). |

**Example**

```ts
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

## ApplicationContext.unregisterAbilityLifecycleCallback<sup>(deprecated)</sup>

unregisterAbilityLifecycleCallback(callbackId: number, callback: AsyncCallback\<void>): void

Unregisters the listener for the in-application UIAbility lifecycle. This API uses an asynchronous callback. Main thread only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [ApplicationContext.off('abilityLifecycle')](js-apis-inner-application-applicationContext.md#applicationcontextoffabilitylifecycle) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name        | Type     | Mandatory | Description                       |
| ------------- | -------- | ---- | -------------------------- |
| callbackId    | number   | Yes   | ID returned when the listener for the in-application UIAbility lifecycle is registered via [ApplicationContext.registerAbilityLifecycleCallback](#applicationcontextregisterabilitylifecyclecallbackdeprecated). |
| callback | AsyncCallback\<void> | Yes   | Callback for the in-application lifecycle event. When the listener for the in-application lifecycle is unregistered successfully, err is undefined; otherwise, err is an error object.   |

**Example**

```ts
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

## ApplicationContext.unregisterAbilityLifecycleCallback<sup>(deprecated)</sup>

unregisterAbilityLifecycleCallback(callbackId: number): Promise\<void>

Unregisters the listener for the in-application UIAbility lifecycle. This API uses a promise to return the result. Main thread only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [ApplicationContext.off('abilityLifecycle')](js-apis-inner-application-applicationContext.md#applicationcontextoffabilitylifecycle) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name        | Type     | Mandatory | Description                       |
| ------------- | -------- | ---- | -------------------------- |
| callbackId    | number   | Yes   | ID returned when the listener for the in-application UIAbility lifecycle is registered via [ApplicationContext.registerAbilityLifecycleCallback](#applicationcontextregisterabilitylifecyclecallbackdeprecated). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise object that returns no value. |

**Example**

```ts
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
## ApplicationContext.registerEnvironmentCallback<sup>(deprecated)</sup>

registerEnvironmentCallback(environmentCallback: EnvironmentCallback): number

Registers a listener for system environment changes. This API uses an asynchronous callback. Main Thread Only.

> **NOTE**
>
> - You can also use [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) to listen for system environment variable changes. Compared with the Ability [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) API, this API is more flexible in usage scenarios. It can be used not only in application components but also in pages. However, the environment variables that can be subscribed to differ from those of the Ability [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) API. For example, subscribing to direction, screenDensity, and displayId is not supported. For details, see the description of each environment variable in [Configuration](../apis-ability-kit/js-apis-app-ability-configuration.md#configuration).
> - This API has certain limitations when actually triggered. For example, if a developer sets the application language through the [setLanguage](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetlanguage11) API, the [environmentCallback](js-apis-app-ability-environmentCallback.md) callback of this API will no longer be triggered even if the system language changes. For details, see [Usage Scenarios](../../application-models/subscribe-system-environment-variable-changes.md#usage-scenarios).
>
> Supported since API version 9, deprecated since API version 10. Recommended to Use [ApplicationContext.on('environment')](js-apis-inner-application-applicationContext.md#applicationcontextonenvironment) as the replacement.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name                   | Type     | Mandatory | Description                           |
| ------------------------ | -------- | ---- | ------------------------------ |
| environmentCallback | [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) | Yes   | Callback invoked when the system environment changes. |

**Return value**

| Type   | Description                                                         |
| ------ | ------------------------------------------------------------ |
| number | ID of the callback registered this time. This ID is used to unregister the corresponding callback in [ApplicationContext.unregisterEnvironmentCallback](#applicationcontextunregisterenvironmentcallbackdeprecated). |

**Example**

```ts
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

## ApplicationContext.unregisterEnvironmentCallback<sup>(deprecated)</sup>

unregisterEnvironmentCallback(callbackId: number, envcallback: AsyncCallback\<void>): void

Unregisters the listener for system environment changes. This API uses an asynchronous callback to return the result. Main Thread Only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [ApplicationContext.off('environment')](js-apis-inner-application-applicationContext.md#applicationcontextoffenvironment) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name         | Type     | Mandatory | Description                       |
| ------------- | -------- | ---- | -------------------------- |
| callbackId    | number   | Yes   | ID returned when the listener for system environment changes is registered via [ApplicationContext.registerEnvironmentCallback](#applicationcontextregisterenvironmentcallbackdeprecated). |
| envcallback | AsyncCallback\<void> | Yes   | Callback for the system environment change event. When the listener for system environment changes is unregistered successfully, err is undefined; otherwise, err is an error object.   |

**Example**

```ts
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

## ApplicationContext.unregisterEnvironmentCallback<sup>(deprecated)</sup>

unregisterEnvironmentCallback(callbackId: number): Promise\<void\>

Unregisters the listener for system environment changes. This API uses a promise to return the result. Main Thread Only.

> **NOTE**
>
> Supported Since API version 9, Deprecated Since API version 10. Recommended to Use [ApplicationContext.off('environment')](js-apis-inner-application-applicationContext.md#applicationcontextoffenvironment) as the replacement.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name         | Type     | Mandatory | Description                       |
| ------------- | -------- | ---- | -------------------------- |
| callbackId    | number   | Yes   | ID returned when the listener for system environment changes is registered via [ApplicationContext.registerEnvironmentCallback](#applicationcontextregisterenvironmentcallbackdeprecated). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise object, no return value. |

**Example**

```ts
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

## ApplicationContext.getProcessRunningInformation<sup>(deprecated)</sup>

getProcessRunningInformation(): Promise\<Array\<ProcessInformation>>

Obtains the information about running processes. This API uses a promise to return the result asynchronously. Main thread only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [ApplicationContext.getRunningProcessInformation](js-apis-inner-application-applicationContext.md#applicationcontextgetrunningprocessinformation) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise object used to return the API execution result and the information about running processes. You can use it for error handling or other custom processing. |

**Error codes**

| ID | Error Message |
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
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

## ApplicationContext.getProcessRunningInformation<sup>(deprecated)</sup>

getProcessRunningInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void

Obtains the information about running processes. This API uses an asynchronous callback to return the result. Main thread only.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [ApplicationContext.getRunningProcessInformation](js-apis-inner-application-applicationContext.md#applicationcontextgetrunningprocessinformation) instead.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name        | Type     | Mandatory | Description                       |
| ------------- | -------- | ---- | -------------------------- |
| callback    | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>>   | Yes   | Callback invoked to return the information about running processes. |

**Error codes**

| ID | Error Message |
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
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