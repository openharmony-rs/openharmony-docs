# @ohos.app.ability.AbilityStage (AbilityStage Component Manager)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=baf3287259f8efd23ff8ec99c9af8cbdb75e24ac translatedAt=2026-09-03T09:52:44.997Z pushedAt=2026-09-05T10:47:30.216Z -->

AbilityStage is a [module](../../../application-dev/quick-start/application-package-overview.md#multi-module-design-mechanism)-level component manager. It is used for initializing operations such as resource preloading and thread creation at the module level, as well as maintaining the application state under the module. An AbilityStage instance corresponds to a module.

When the [HAP](../../../application-dev/quick-start/hap-package.md) or [HSP](../../../application-dev/quick-start/in-app-hsp.md) of an application is first loaded, an AbilityStage instance is created. If a module contains both AbilityStage and other components (like UIAbility or ExtensionAbility), the AbilityStage instance is created before the other component instances.

An AbilityStage has the lifecycle callbacks [onCreate()](#oncreate) and [onDestroy()](#ondestroy12), and the event callbacks [onAcceptWant()](#onacceptwant), [onConfigurationUpdate()](#onconfigurationupdate), and [onMemoryLevel()](#onmemorylevel).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { AbilityStage } from '@kit.AbilityKit';
```

## AbilityStage

### Properties

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context  | [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | No| No| Context of an AbilityStage.|

### onCreate

onCreate(): void

Called when an AbilityStage instance is created. Such an instance is automatically created by the system before it loads the first Ability instance of the module.

You can initialize the module (for example, preload resources or create threads) in this callback. This API returns the result synchronously and does not support asynchronous callbacks.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    console.info('MyAbilityStage.onCreate is called');
  }
}
```


### onAcceptWant

onAcceptWant(want: Want): string

Called when a UIAbility with the launch mode set to [specified](../../application-models/uiability-launch-type.md#specified) is launched. This API returns a string representing the unique ID of the UIAbility instance. This API returns the result synchronously and does not support asynchronous callbacks.

If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created.

> **NOTE**
>
> Starting from API version 20, this callback is not triggered when [AbilityStage.onAcceptWantAsync](#onacceptwantasync20) is implemented.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want type parameter, indicating the startup parameters passed by the caller, such as the ability name and bundle name. |

**Return value**

| Type| Description|
| -------- | -------- |
| string | ID of the UIAbility. If a UIAbility with the same ID has been launched, that UIAbility is reused. Otherwise, a new instance is created and launched.|

**Example**


```ts
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAcceptWant(want: Want) {
    console.info('MyAbilityStage.onAcceptWant called');
    return 'com.example.test';
  }
}
```

### onNewProcessRequest<sup>11+</sup>

onNewProcessRequest(want: Want): string

Called when a UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd-->, which is configured to run in an independent process (with **isolationProcess** set to **true** in the [module.json5](../../quick-start/module-configuration-file.md) file), is launched. This API returns a string representing the unique process ID. This API returns the result synchronously and does not support asynchronous callbacks.

If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> runs in that process. Otherwise, a new process is created.

If you implement both **onNewProcessRequest** and [onAcceptWant](#onacceptwant), the system first invokes the **onNewProcessRequest** callback, and then the **onAcceptWant** callback.

<!--Del-->
The **isolationProcess** field can be set to **true** in the [module.json5](../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of the sys/commonUI type.
<!--DelEnd-->

> **NOTE**
>
> - In API version 19 and earlier, only a UIAbility can be launched in the specified process. <!--Del-->Starting from API version 20, a UIExtensionAbility can also be launched in the specified process.<!--DelEnd-->
> - Starting from API version 20, this callback is not executed when [AbilityStage.onNewProcessRequestAsync](#onnewprocessrequestasync20) is implemented.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**:
- Since API version 12, this API executes the callback normally on tablet devices, but does not execute the callback on other devices.
- Since API version 13, this API executes the callback normally on PCs, 2-in-1 devices, and tablets, but does not execute the callback on other devices.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want type parameter that includes the launch parameters provided by the caller, such as the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> name and bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | A process string identifier determined by the developer. If the process corresponding to this identifier has already been created, the Ability runs in this process; otherwise, a new process is created. |

**Example**

```ts
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onNewProcessRequest(want: Want) {
    console.info('MyAbilityStage.onNewProcessRequest called');
    return 'com.example.test';
  }
}
```


### onConfigurationUpdate

onConfigurationUpdate(newConfig: Configuration): void

Called when the system global configuration (such as the system language and dark/light color mode) changes. All the configuration items are defined in the [Configuration](../../../application-dev/reference/apis-ability-kit/js-apis-app-ability-configuration.md) class. This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE**
>
> There are certain restrictions when this callback is actually triggered. For example, if you set the application language by calling [setLanguage](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetlanguage11), the system does not trigger the **onConfigurationUpdate** callback even if the system language changes. For details, see [When to Use](../../application-models/subscribe-system-environment-variable-changes.md#when-to-use).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | newConfig | [Configuration](js-apis-app-ability-configuration.md) | Yes| Callback invoked when the global configuration is updated. The global configuration indicates the configuration of the environment where the application is running and includes the language and color mode.|

**Example**

```ts
import { AbilityStage, Configuration } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onConfigurationUpdate(config: Configuration) {
    console.info(`MyAbilityStage.onConfigurationUpdate, language: ${config.language}`);
  }
}
```

### onMemoryLevel

onMemoryLevel(level: AbilityConstant.MemoryLevel): void

Listens for changes in the system memory level status. Called when the available memory of the entire device changes to a specified level. You can implement this callback to promptly release non-essential resources (such as cached data or temporary objects) upon receiving a memory shortage event, thereby preventing the application process from being forcibly terminated by the system.

This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE**
> 
> The onMemoryLevel callback runs in the main thread of the current process. If time-consuming UI component release is performed in this callback, the main thread tasks will be blocked. Therefore, it is not recommended to release UI components in this callback.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | level | [AbilityConstant.MemoryLevel](js-apis-app-ability-abilityConstant.md#memorylevel) | Yes | Memory level of the entire device. For details about the corresponding trigger scenarios, see [AbilityConstant.MemoryLevel](js-apis-app-ability-abilityConstant.md#memorylevel).|

**Example**

```ts
import { AbilityStage, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`MyAbilityStage.onMemoryLevel, level: ${JSON.stringify(level)}`);
  }
}
```

### onDestroy<sup>12+</sup>

onDestroy(): void

Called when the last Ability instance of the corresponding module exits. This API is called during the normal lifecycle. If the application exits abnormally or is terminated, this API is not called. This API returns the result synchronously and does not support asynchronous callbacks.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onDestroy() {
    console.info('MyAbilityStage.onDestroy is called');
  }
}
```

### onPrepareTermination<sup>15+</sup>

onPrepareTermination(): AbilityConstant.PrepareTermination

Called when the application is closed by the user, allowing the user to choose between immediate termination or cancellation. This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE**
>
> - This API is called only when the application exits under normal circumstances (for example, when the application is closed through the task bar or tray, or when the application exits as the device shuts down). If the application is forcibly closed, this API is not called.
>
> - When [AbilityStage.onPrepareTerminationAsync](#onprepareterminationasync15) is implemented, this callback function is not executed.

**Required permissions**: ohos.permission.PREPARE_APP_TERMINATE

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**
- Starting from API version 15, this API executes the callback normally only on PC/2-in-1 devices. It does not execute the callback on other devices.
- Starting from API version 19, this API executes the callback normally only on PC/2-in-1 devices and tablets. It does not execute the callback on other devices.

**Return value**

| Type| Description|
| -------- | -------- |
| [AbilityConstant.PrepareTermination](js-apis-app-ability-abilityConstant.md#preparetermination15) | The user's choice.|

**Example**

```ts
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onPrepareTermination(): AbilityConstant.PrepareTermination {
    console.info('MyAbilityStage.onPrepareTermination is called');
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```

### onPrepareTerminationAsync<sup>15+</sup>

onPrepareTerminationAsync(): Promise\<AbilityConstant.PrepareTermination>

Called when the application is closed by the user, allowing the user to choose between immediate termination or cancellation. This API uses a promise to return the result.

> **NOTE**
>
> - This API is called only when the application exits under normal circumstances (for example, when the application is closed through the task bar or tray, or when the application exits as the device shuts down). If the application is forcibly closed, this API is not called.
>
> - If a crash occurs in the asynchronous callback, it is handled as a timeout. If no response is received after waiting for more than 10 seconds, the application is forcibly closed.

**Required permissions**: ohos.permission.PREPARE_APP_TERMINATE

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**
- Starting from API version 15, this API executes the callback normally only on PC/2-in-1 devices. It does not execute the callback on other devices.
- Starting from API version 19, this API executes the callback normally only on PC/2-in-1 and tablet devices. It does not execute the callback on other devices.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<[AbilityConstant.PrepareTermination](js-apis-app-ability-abilityConstant.md#preparetermination15)> | Promise used to return the user's choice.|

**Example**

```ts
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  async onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination> {
    await new Promise<AbilityConstant.PrepareTermination>((res, rej) => {
      setTimeout(res, 3000); // Execute the operation after 3 seconds.
    });
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```

### onAcceptWantAsync<sup>20+</sup>

onAcceptWantAsync(want: Want): Promise\<string\>

Called when a UIAbility with the launch mode set to [specified](../../application-models/uiability-launch-type.md#specified) is launched. This API returns a string representing the unique ID of the UIAbility instance. This API uses a promise to return the result.

If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want information about the target UIAbility, such as the UIAbility name and bundle name.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise\<string\> | Promise used to return a string that uniquely identifies the UIAbility instance launched. If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created.|

**Example**

```ts
import { AbilityStage, Want } from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  async onAcceptWantAsync(want: Want): Promise<string> {
    await new Promise<string>((res, rej) => {
      setTimeout(res, 1000); // Execute the operation after 1 second.
      console.info(`onAcceptWantAsync, want: ${JSON.stringify(want)}`);
    });
    return 'default';
  }
}
```

### onNewProcessRequestAsync<sup>20+</sup>

onNewProcessRequestAsync(want: Want): Promise\<string\>

Called when a UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd-->, which is configured to run in an independent process (with **isolationProcess** set to **true** in the [module.json5](../../quick-start/module-configuration-file.md) file), is launched. This API returns a string representing the unique process ID. This API uses a promise to return the result.

If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> runs in that process. Otherwise, a new process is created.

<!--Del-->
The **isolationProcess** field can be set to **true** in the [module.json5](../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of the sys/commonUI type.
<!--DelEnd-->

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device Behavior**: This API executes the callback normally only on PC/2-in-1 and tablet devices. It does not execute the callback on other devices.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes| Want type parameter that includes the launch parameters provided by the caller, such as the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> name and bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<string\> | Promise used to return a string representing the process ID. If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> runs in that process. Otherwise, a new process is created.|

**Example**

```ts
import { AbilityStage, Want } from '@kit.AbilityKit';

class MyAbilityStage extends AbilityStage {
  async onNewProcessRequestAsync(want: Want): Promise<string> {
    await new Promise<string>((res, rej) => {
      setTimeout(res, 1000); // Execute the operation after 1 second.
      console.info(`onNewProcessRequestAsync, want: ${JSON.stringify(want)}`);
    });
    return '';
  }
}
```

### onLaunchFromHyperSnap<sup>24+</sup>

onLaunchFromHyperSnap(): void

Called when the process is launched from [application quick launch](./js-apis-app-ability-hyperSnapManager.md#implementation-principle).

Developers can override this method to handle specific logic during application quick launch, for example, reinitializing certain resources or states.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onLaunchFromHyperSnap(): void {
    console.info('Launched from Hyper Snap, reinitializing resources...');
    // Add the initialization logic for quick startup here.
  }
}
```

### onAboutToCreateAbility<sup>24+</sup>

onAboutToCreateAbility(): void

Called when the AbilityStage is about to create the first Ability.

Developers can override this method to perform preparations before the first Ability is created.

> **NOTE**
>
> - Since API version 26.0.0, if [AbilityStage.onAboutToCreateAbilityAsync](#onabouttocreateabilityasync) is implemented, this callback function will not be triggered.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAboutToCreateAbility(): void {
    console.info('About to create first ability, preparing...');
    // Add the preparation work before creating the first ability here.
  }
}
```

### onAboutToCreateAbilityAsync

onAboutToCreateAbilityAsync(): Promise\<void\>

Called when the AbilityStage is about to create the first ability. This API uses a promise to return the result asynchronously.

The subsequent lifecycle callbacks are executed only after the promise returned by this method is resolved successfully; otherwise, they are suspended.

By overriding this method, developers can perform necessary asynchronous initialization and preparation before the AbilityStage creates the first ability.

**Since:** 26.0.0

> **NOTE**
>
> If both [onAboutToCreateAbility](#onabouttocreateability24) and this method are implemented, only this method takes effect.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void\> | Promise object that returns no value. The subsequent lifecycle callbacks are executed only after the promise is resolved successfully. |

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  async onAboutToCreateAbilityAsync(): Promise<void> {
    console.info('About to create first ability, preparing...');
    // Perform the asynchronous initialization.
    await new Promise<void>((resolve) => {
      setTimeout(() => {
        console.info('Async preparation completed');
        resolve();
      }, 1000);
    });
    // The ability is created only after the initialization is complete.
  }
}
```
