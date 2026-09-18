# AbilityStage

AbilityStage is a [module](../../../quick-start/application-package-overview.md#multi-module-design-mechanism)-level component manager. It is used for initializing operations such as resource preloading and thread creation at the module level, as well as maintaining the application state under the module. An AbilityStage instance corresponds to a module.

When the [HAP](../../../quick-start/hap-package.md) or [HSP](../../../quick-start/in-app-hsp.md) of an application is first loaded, an AbilityStage instance is created. If a module contains both AbilityStage and other components (like UIAbility or ExtensionAbility), the AbilityStage instance is created before the other component instances.

An AbilityStage has the lifecycle callbacks [onCreate()](#oncreate) and [onDestroy()](#ondestroy), and the event callbacks [onAcceptWant()](#onacceptwant), [onConfigurationUpdate()](#onconfigurationupdate), and [onMemoryLevel()](#onmemorylevel).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';
```

## onAboutToCreateAbility

```TypeScript
onAboutToCreateAbility(): void
```

Called when the ability stage is about to create the first ability. If both this method and [onAboutToCreateAbilityAsync](#onabouttocreateabilityasync) are overridden, only [onAboutToCreateAbilityAsync](#onabouttocreateabilityasync) takes effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAboutToCreateAbility(): void {
    console.info('About to create first ability, preparing...');
    // Add the preparation work before creating the first ability here.
  }
}
```

## onAboutToCreateAbilityAsync

```TypeScript
onAboutToCreateAbilityAsync(): Promise<void>
```

Called when the ability stage is about to create the first ability. This API uses a promise to return the result. Subsequent lifecycle callbacks will be suspended until the returned Promise is resolved. If both [onAboutToCreateAbility](#onabouttocreateability) and this method are overridden, only this method takes effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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

## onAcceptWant

```TypeScript
onAcceptWant(want: Want): string
```

Called when a UIAbility with the launch mode set to [specified](../../../application-models/uiability-launch-type.md#specified) is launched. This API returns a string representing the unique ID of the UIAbility instance. This API returns the result synchronously and does not support asynchronous callbacks.

If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created.

> **NOTE:** 
> 
> Starting from API version 20, this callback is not triggered when
> [AbilityStage.onAcceptWantAsync](#onacceptwantasync) is implemented.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want type parameter that includes the launch parameters provided by the caller, such as the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the UIAbility. If a UIAbility with the same ID has been launched, that UIAbility is reused. Otherwise, a new instance is created and launched. |

**Examples**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onAcceptWant(want: Want) {
    console.info('MyAbilityStage.onAcceptWant called');
    return 'com.example.test';
  }
}
```

## onAcceptWantAsync

```TypeScript
onAcceptWantAsync(want: Want): Promise<string>
```

Called when a UIAbility with the launch mode set to [specified](../../../application-models/uiability-launch-type.md#specified) is launched. This API returns a string representing the unique ID of the UIAbility instance. This API uses a promise to return the result.

If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target UIAbility, such as the UIAbility name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return a string that uniquely identifies the UIAbility instance launched. If a UIAbility instance with the same ID already exists in the system, that instance is reused. Otherwise, a new instance is created. |

**Examples**

```TypeScript
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

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

Called when the system global configuration (such as the system language and dark/light color mode) changes. All the configuration items are defined in the [Configuration](arkts-ability-app-ability-configuration-configuration-i.md) class. This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE:** 
> 
> There are certain restrictions when this callback is actually triggered. For example, if you set the application
> language by calling [setLanguage](arkts-ability-applicationcontext-c.md#setlanguage), the
> system does not trigger the **onConfigurationUpdate** callback even if the system language changes. For details,
> see [When to Use](../../../application-models/subscribe-system-environment-variable-changes.md#when-to-use).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newConfig | [Configuration](arkts-ability-app-ability-configuration-configuration-i.md) | Yes | Callback invoked when the global configuration is updated. The global configuration indicates the configuration of the environment where the application is running and includes the language and color mode. |

**Examples**

```TypeScript
import { AbilityStage, Configuration } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onConfigurationUpdate(config: Configuration) {
    console.info(`MyAbilityStage.onConfigurationUpdate, language: ${config.language}`);
  }
}
```

## onCreate

```TypeScript
onCreate(): void
```

Called when an AbilityStage instance is created. Such an instance is automatically created by the system before it loads the first Ability instance of the module.

You can initialize the module (for example, preload resources or create threads) in this callback. This API returns the result synchronously and does not support asynchronous callbacks.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    console.info('MyAbilityStage.onCreate is called');
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Called when the last Ability instance of the corresponding module exits. This API is called during the normal lifecycle. If the application exits abnormally or is terminated, this API is not called. This API returns the result synchronously and does not support asynchronous callbacks.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onDestroy() {
    console.info('MyAbilityStage.onDestroy is called');
  }
}
```

## onLaunchFromHyperSnap

```TypeScript
onLaunchFromHyperSnap(): void
```

Called when the process is launched from HyperSnap.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onLaunchFromHyperSnap(): void {
    console.info('Launched from Hyper Snap, reinitializing resources...');
    // Add the initialization logic for quick startup here.
  }
}
```

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

Listens for changes in the system memory level status. Called when the available memory of the entire device changes to a specified level. You can implement this callback to promptly release non-essential resources (such as cached data or temporary objects) upon receiving a memory shortage event, thereby preventing the application process from being forcibly terminated by the system.

This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE:** 
> 
> Releasing UI components in the **onMemoryLevel** callback may block the main thread tasks of the current process.
> Therefore, you are advised not to release UI components in this callback.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [AbilityConstant.MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md) | Yes | Memory level that indicates the memory usage status. When the specified memory level is reached, a callback will be invoked and the system will start adjustment.<br>**NOTE:** <br>The trigger conditions may differ across various devices. For example, on a standard device with 12 GB of memory:<br>- A callback with value 0 is triggered when available memory drops between 1700 MB and 1800 MB.<br>- A callback with value 1 is triggered when available memory drops between 1600 MB and 1700 MB.<br>- A callback with value 2 is triggered when available memory falls below 1600 MB. |

**Examples**

```TypeScript
import { AbilityStage, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`MyAbilityStage.onMemoryLevel, level: ${JSON.stringify(level)}`);
  }
}
```

## onNewProcessRequest

```TypeScript
onNewProcessRequest(want: Want): string
```

Called when a UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd-->, which is configured to run in an independent process (with **isolationProcess** set to **true** in the [module.json5](../../../quick-start/module-configuration-file.md) file), is launched. This API returns a string representing the unique process ID. This API returns the result synchronously and does not support asynchronous callbacks.

If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd- -> runs in that process. Otherwise, a new process is created.

If you implement both **onNewProcessRequest** and [onAcceptWant](#onacceptwant), the system first invokes the **onNewProcessRequest** callback, and then the **onAcceptWant** callback.

<!--Del-->

The **isolationProcess** field can be set to **true** in the [module.json5](../../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of the sys/commonUI type.

<!--DelEnd-->

> **NOTE:** 
> 
> - In API version 19 and earlier, only a UIAbility can be launched in the specified process. <!--Del-->Starting from API version 20, a UIExtensionAbility can also be launched in the specified process.<!--DelEnd-->
> 
> - Starting from API version 20, this callback is not executed when [AbilityStage.onNewProcessRequestAsync](#onnewprocessrequestasync) is implemented.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want type parameter that includes the launch parameters provided by the caller, such as the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Custom process identifier. If the process with this identifier has been created, the ability runs in the process. Otherwise, a new process is created and the ability runs in it. |

**Examples**

```TypeScript
import { AbilityStage, Want } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onNewProcessRequest(want: Want) {
    console.info('MyAbilityStage.onNewProcessRequest called');
    return 'com.example.test';
  }
}
```

## onNewProcessRequestAsync

```TypeScript
onNewProcessRequestAsync(want: Want): Promise<string>
```

Called when a UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd-->, which is configured to run in an independent process (with **isolationProcess** set to **true** in the [module.json5](../../../quick-start/module-configuration-file.md) file), is launched. This API returns a string representing the unique process ID. This API uses a promise to return the result.

If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd- -> runs in that process. Otherwise, a new process is created.

<!--Del-->

The **isolationProcess** field can be set to **true** in the [module.json5](../../../quick-start/module-configuration-file.md) file, but only for the UIExtensionAbility of the sys/commonUI type.

<!--DelEnd-->

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want type parameter that includes the launch parameters provided by the caller, such as the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return a string representing the process ID. If the application already has a process with the same ID, the UIAbility<!--Del--> or UIExtensionAbility<!--DelEnd--> runs in that process. Otherwise, a new process is created. |

**Examples**

```TypeScript
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

## onPrepareTermination

```TypeScript
onPrepareTermination(): AbilityConstant.PrepareTermination
```

Called when the application is closed by the user, allowing the user to choose between immediate termination or cancellation. This API returns the result synchronously and does not support asynchronous callbacks.

> **NOTE:** 
> 
> - The API is called only when the application exits under normal circumstances (for example, when the application is closed through the doc bar or tray, or when the application shuts down along with the device). It will not be called if the application is terminated forcibly.
> 
> - This API is not executed when [AbilityStage.onPrepareTerminationAsync](#onprepareterminationasync) is implemented.

**Since:** 15

**Required permissions:** ohos.permission.PREPARE_APP_TERMINATE

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityConstant.PrepareTermination](arkts-ability-abilityconstant-preparetermination-e.md) | The user's choice. |

**Examples**

```TypeScript
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onPrepareTermination(): AbilityConstant.PrepareTermination {
    console.info('MyAbilityStage.onPrepareTermination is called');
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```

## onPrepareTerminationAsync

```TypeScript
onPrepareTerminationAsync(): Promise<AbilityConstant.PrepareTermination>
```

Called when the application is closed by the user, allowing the user to choose between immediate termination or cancellation. This API uses a promise to return the result.

> **NOTE:** 
> 
> - The API is called only when the application exits under normal circumstances (for example, when the application is closed through the doc bar or tray, or when the application shuts down along with the device). It will not be called if the application is terminated forcibly.
> 
> - If an asynchronous callback crashes, it will be handled as a timeout. If the application does not respond within 10 seconds, it will be terminated forcibly.

**Since:** 15

**Required permissions:** ohos.permission.PREPARE_APP_TERMINATE

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityConstant.PrepareTermination](arkts-ability-abilityconstant-preparetermination-e.md)&gt; | Promise used to return the user's choice. |

**Examples**

```TypeScript
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

## context

```TypeScript
context: AbilityStageContext
```

Context of an AbilityStage.

**Type:** [AbilityStageContext](arkts-ability-abilitystagecontext-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
