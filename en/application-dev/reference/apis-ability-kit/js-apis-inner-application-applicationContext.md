# ApplicationContext (Application Context)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=61ad959070e22c282830a1b55fa1ebaedbcf0ce4 translatedAt=2026-09-09T03:11:34.759Z pushedAt=2026-09-09T03:52:08.743Z -->

ApplicationContext inherits from [Context](js-apis-inner-application-context.md) and provides application-level management capabilities, such as application lifecycle listening, process management, and application environment setting.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## ApplicationContext.on('abilityLifecycle')

on(type: 'abilityLifecycle', callback: AbilityLifecycleCallback): number

Registers a listener for the lifecycle of a UIAbility within the application. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                  | Type    | Mandatory| Description                          |
| ------------------------ | -------- | ---- | ------------------------------ |
| type | string | Yes  | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**.|
| callback | [AbilityLifecycleCallback](js-apis-app-ability-abilityLifecycleCallback.md) | Yes  | Callback triggered when the UIAbility lifecycle changes.|

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.off('abilityLifecycle')](#applicationcontextoffabilitylifecycle).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
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

    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener for the in-application lifecycle through applicationContext.
      lifecycleId = applicationContext.on('abilityLifecycle', abilityLifecycleCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerAbilityLifecycleCallback lifecycleId: ${lifecycleId}`);
  }

  // Unregister the listener for the in-application UIAbility lifecycle when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain the applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
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

## ApplicationContext.off('abilityLifecycle')

off(type: 'abilityLifecycle', callbackId: number,  callback: AsyncCallback\<void>): void

Unregisters a listener for the lifecycle of a UIAbility within the application. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| type | string | Yes  | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**.|
| callbackId    | number   | Yes  | ID returned when the [ApplicationContext.on('abilityLifecycle')](#applicationcontextonabilitylifecycle) API is called to register a listener for the lifecycle of a UIAbility within the application.|
| callback | AsyncCallback\<void> | Yes | Callback for the lifecycle event of the in-application UIAbility. When the listener for the lifecycle of the in-application UIAbility is unregistered successfully, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // Unregister the listener for the in-application UIAbility lifecycle.
      applicationContext.off('abilityLifecycle', lifecycleId, (error, data) => {
        if (error) {
          console.error(`unregisterAbilityLifecycleCallback fail, err: ${JSON.stringify(error)}`);
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

## ApplicationContext.off('abilityLifecycle')

off(type: 'abilityLifecycle', callbackId: number): Promise\<void>

Unregisters a listener for the lifecycle of a UIAbility within the application. This API uses a promise to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| type | string | Yes  | Lifecycle of the UIAbility within the application. The value is fixed at **'abilityLifecycle'**.|
| callbackId    | number   | Yes  | ID returned when the [ApplicationContext.on('abilityLifecycle')](#applicationcontextonabilitylifecycle) API is called to register a listener for the lifecycle of a UIAbility within the application.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let lifecycleId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    console.info(`stage applicationContext: ${applicationContext}`);
    try {
      // Unregister the listener for the in-application UIAbility lifecycle.
      applicationContext.off('abilityLifecycle', lifecycleId);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ApplicationContext.on('environment')

on(type: 'environment', callback: EnvironmentCallback): number

Registers a listener for system environment changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> - You can also use [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) to listen for system environment changes. Unlike [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) of **Ability**, this API offers greater flexibility. It can be used both within application components and pages. However, the environment variables that can be subscribed to are different from those of [onConfigurationUpdate](../apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate). For example, this API cannot be used to subscribe to direction, screen density, and display ID changes. For details, see the description of each environment variable in [Configuration](../apis-ability-kit/js-apis-app-ability-configuration.md#configuration).
> - There are certain restrictions when this API is triggered. For example, if you set the application language by calling [setLanguage](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetlanguage11), the system does not trigger the callback for the current API even if the system language changes. For details, see [When to Use](../../application-models/subscribe-system-environment-variable-changes.md#when-to-use).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                  | Type    | Mandatory| Description                          |
| ------------------------ | -------- | ---- | ------------------------------ |
| type | string | Yes  | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**.|
| callback | [EnvironmentCallback](js-apis-app-ability-environmentCallback.md) | Yes  | Callback triggered when the system environment changes.|

**Return value**

| Type  | Description                                                        |
| ------ | ------------------------------------------------------------ |
| number | ID of the callback registered. This ID is used to unregister the corresponding callback in [ApplicationContext.off('environment')](#applicationcontextoffenvironment).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

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
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener for system environment changes through applicationContext.
      callbackId = applicationContext.on('environment', environmentCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info(`registerEnvironmentCallback callbackId: ${callbackId}`);
  }

  // Unregister the listener for system environment changes when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
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

## ApplicationContext.off('environment')

off(type: 'environment', callbackId: number,  callback: AsyncCallback\<void>): void

Unregisters the listener for system environment changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name        | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| type | string | Yes  | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**.|
| callbackId    | number   | Yes  | ID returned when the [ApplicationContext.on('environment')](#applicationcontextonenvironment) API is called to register a listener for system environment changes.|
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the deregistration is successful, **err** is **undefined**. Otherwise, **err** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class EntryAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener for system environment changes.
      applicationContext.off('environment', callbackId, (error, data) => {
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

## ApplicationContext.off('environment')

off(type: 'environment', callbackId: number): Promise\<void\>

Unregisters the listener for system environment changes. This API uses a promise to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name        | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| type | string | Yes  | System environment change, for example, system dark/light color mode change. The value is fixed at **'environment'**.|
| callbackId    | number   | Yes  | ID returned when the [ApplicationContext.on('environment')](#applicationcontextonenvironment) API is called to register a listener for system environment changes.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackId: number;

export default class MyAbility extends UIAbility {
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener for system environment changes.
      applicationContext.off('environment', callbackId);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ApplicationContext.on('applicationStateChange')<sup>10+</sup>

on(type: 'applicationStateChange', callback: ApplicationStateChangeCallback): void

Registers a listener for application process state changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description            |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| type     | string                                   | Yes  | Application process state change. The value is fixed at **'applicationStateChange'**.|
| callback | [ApplicationStateChangeCallback](js-apis-app-ability-applicationStateChangeCallback.md) | Yes   | Callback invoked when the current application process state changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateChangeCallback: ApplicationStateChangeCallback = {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  },
  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
}

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener for the current application process state through applicationContext.
      applicationContext.on('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info('Register applicationStateChangeCallback');
  }

  // Unregister all listeners of this event type when they are no longer needed or when the application exits.
  onDestroy() {
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.off('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ApplicationContext.off('applicationStateChange')<sup>10+</sup>

off(type: 'applicationStateChange', callback?: ApplicationStateChangeCallback): void

Unregisters the listener for application process state changes. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| type   |  string                                   | Yes  | Application process state change. The value is fixed at **'applicationStateChange'**.|
| callback | [ApplicationStateChangeCallback](js-apis-app-ability-applicationStateChangeCallback.md) | No  | Callback used to return the result. The value can be a callback defined by [ApplicationContext.on('applicationStateChange')](#applicationcontextonapplicationstatechange10) or empty.<br>- If a defined callback is passed in, the listener for that callback is unregistered.<br>- If no value is passed in, all the listeners for the corresponding event are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

Assume that [ApplicationContext.on('applicationStateChange')](#applicationcontextonapplicationstatechange10) is used to register a callback named **applicationStateChangeCallback**. The following example shows how to unregister the corresponding listener.

```ts
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
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // In this example, the callback field is set to applicationStateChangeCallback.
      // If no value is passed in, all the listeners for the corresponding event are unregistered.
      applicationContext.off('applicationStateChange', applicationStateChangeCallback);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ApplicationContext.onSystemConfigurationUpdated<sup>24+</sup>

onSystemConfigurationUpdated(callback: systemConfiguration.UpdatedCallback): void

Registers a listener for changes in the system environment [Configuration](js-apis-app-ability-configuration.md#configuration). This API uses an asynchronous callback to return the result. This API can be called only on the main thread.

> **NOTE**
>
> Custom settings of the application do not affect the triggering of the callback function. For example, if the application has customized the dark/light color mode, the registered callback function is still triggered when the system dark/light color mode changes.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                   | Type     | Mandatory | Description                           |
| ------------------------ | -------- | ---- | ------------------------------ |
| callback | [systemConfiguration.UpdatedCallback](js-apis-app-ability-systemConfiguration.md#updatedcallback) | Yes   | Callback method triggered when the system environment changes. |

**Example**

```ts
import { UIAbility, systemConfiguration, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

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

export default class EntryAbility extends UIAbility {
  onForeground() {
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register a listener through applicationContext.
      applicationContext.onSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`onSystemConfigurationUpdated finish`);
  }

  // Unregister the listener when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Unregister the listener through applicationContext.
      applicationContext.offSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```

## ApplicationContext.offSystemConfigurationUpdated<sup>24+</sup>

offSystemConfigurationUpdated(callback?: systemConfiguration.UpdatedCallback): void

Unregisters the listener for changes to the system environment [Configuration](js-apis-app-ability-configuration.md#configuration). This API can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name                   | Type     | Mandatory | Description                           |
| ------------------------ | -------- | ---- | ------------------------------ |
| callback | [systemConfiguration.UpdatedCallback](js-apis-app-ability-systemConfiguration.md#updatedcallback) | No   | Callback function. The value can be the callback registered using the [ApplicationContext.onSystemConfigurationUpdated](#applicationcontextonsystemconfigurationupdated24) method, or it can be empty.<br/>-&nbsp;If a defined callback is passed in, the listener is unregistered. <br/>-&nbsp;If no parameter is passed in, all registered listeners are unregistered.|

**Example**

```ts
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
    // 1. Obtain applicationContext through the context attribute.
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Unregister the listener through applicationContext.
      applicationContext.offSystemConfigurationUpdated(callBack);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info(`offSystemConfigurationUpdated finish`);
  }
}
```

## ApplicationContext.getRunningProcessInformation

getRunningProcessInformation(): Promise\<Array\<ProcessInformation>>

Obtains the information about running processes. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Obtain the running process information.
    applicationContext.getRunningProcessInformation().then((data) => {
      console.info(`The process running information is: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
      console.error(`error code: ${error.code}, error msg: ${error.message}`);
    });
  }
}
```

## ApplicationContext.getRunningProcessInformation

getRunningProcessInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void

Obtains the information about running processes. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| callback    | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>>   | Yes   | Callback used to obtain the running process information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onForeground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Obtain the running process information.
    applicationContext.getRunningProcessInformation((err, data) => {
      if (err) {
        console.error(`getRunningProcessInformation failed, err: ${JSON.stringify(err)}`);
      } else {
        console.info(`The process running information is: ${JSON.stringify(data)}`);
      }
    })
  }
}
```

## ApplicationContext.killAllProcesses

killAllProcesses(): Promise\<void\>

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call [terminateSelf()](js-apis-inner-application-uiAbilityContext.md#terminateself-1).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application.
    applicationContext.killAllProcesses();
  }
}
```

## ApplicationContext.killAllProcesses<sup>14+</sup>

killAllProcesses(clearPageStack: boolean): Promise\<void\>

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses a promise to return the result. It can be called only on the main thread.

> **NOTE**
>
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call [terminateSelf()](js-apis-inner-application-uiAbilityContext.md#terminateself-1).

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| clearPageStack | boolean | Yes| Whether to clear the page stack. **true** to clear, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | If the input parameter is not valid parameter. |
| 16000011 | The context does not exist. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

let isClearPageStack = false;

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application and clear the page stack.
    applicationContext.killAllProcesses(isClearPageStack);
  }
}
```

## ApplicationContext.killAllProcesses

killAllProcesses(callback: AsyncCallback\<void\>): void

Kills all processes of this application. The application will not execute the normal lifecycle when exiting. This API uses an asynchronous callback to return the result. It can be called only on the main thread.

> **NOTE**
>
> This API is used to forcibly exit an application in abnormal scenarios. To exit an application properly, call [terminateSelf()](js-apis-inner-application-uiAbilityContext.md#terminateself-1).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| callback    | AsyncCallback\<void\>   | Yes   | Callback function. When all processes of the application are terminated successfully, err is undefined; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Terminate all processes of the application.
    applicationContext.killAllProcesses(error => {
      if (error) {
        console.error(`killAllProcesses fail, error: ${JSON.stringify(error)}`);
      }
    });
  }
}
```
## ApplicationContext.setColorMode<sup>11+</sup>

setColorMode(colorMode: ConfigurationConstant.ColorMode): void

Sets the dark/light color mode for the application. This API can be called only on the main thread.

> **NOTE**
>
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has been loaded (using the [loadContent](../apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) API in the [onWindowStageCreate()](js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| colorMode | [ConfigurationConstant.ColorMode](js-apis-app-ability-configurationConstant.md#colormode) | Yes | Dark or light color mode, including dark mode, light mode, and unset color mode (default). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |

**Example**

```ts
import { UIAbility, ConfigurationConstant } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
      // Obtain the application context.
      let applicationContext = this.context.getApplicationContext();
      // Set the application to dark mode.
      applicationContext.setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
    });
  }
}
```

## ApplicationContext.setLanguage<sup>11+</sup>

setLanguage(language: string): void

Sets the language for the application. This API can be called only on the main thread.

> **NOTE**
>
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has been loaded (using the [loadContent](../apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) API in the [onWindowStageCreate()](js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| language | string | Yes  | Target language. The list of supported languages can be obtained by calling [getSystemLanguages()](../apis-localization-kit/js-apis-i18n.md#getsystemlanguages9). |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    console.info("Ability onWindowStageCreate");
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Set the application language to Chinese.
    applicationContext.setLanguage('zh-cn');
  }
}
```

## ApplicationContext.clearUpApplicationData<sup>11+</sup>

clearUpApplicationData(): Promise\<void\>

Clears up all data in the application file path and revokes the permissions that the application has requested from users. This API uses a promise to return the result. It can be called only on the main thread.


> **NOTE**
> 
> For details about the application file path, see [Application File Directory and Application File Path](../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path). The figure shows only the application file paths in the EL1 and EL2 directories. For the application file paths in other directories, refer to EL1.
>
> This API stops the application process. After the application process is stopped, all subsequent callbacks will not be triggered.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Clear all data under the application file path of the current application.
    applicationContext.clearUpApplicationData();
  }
}
```

## ApplicationContext.clearUpApplicationData<sup>11+</sup>

clearUpApplicationData(callback: AsyncCallback\<void\>): void

Clears up all data in the application file path and revokes the permissions that the application has requested from users. This API uses an asynchronous callback to return the result. It can be called only on the main thread.


> **NOTE**
> 
> For details about the application file path, see [Application File Directory and Application File Path](../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path). The figure shows only the application file paths in the EL1 and EL2 directories. For the application file paths in other directories, refer to EL1.
>
> This API stops the application process. After the application process is stopped, all subsequent callbacks will not be triggered.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| callback | AsyncCallback\<void> | Yes   | Callback invoked when all data in the application file path of the current application is cleared and the permissions requested by the application from the user are revoked successfully. In this case, error is undefined; otherwise, an error object is returned.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    // Clear all data under the application file path of the current application.
    applicationContext.clearUpApplicationData(error => {
      if (error) {
        console.error(`clearUpApplicationData fail, error: ${JSON.stringify(error)}`);
      }
    });
  }
}
```

## ApplicationContext.restartApp<sup>12+</sup>

restartApp(want: Want): void

Restarts the application and starts the specified UIAbility. This API can be called only by the main thread, and the application to restart must be active.

> **NOTE**
>
> When this API is called to restart the application, the **onDestroy** lifecycle callback of the ability in the application is not triggered.
>
> If an atomic service calls this API, [restartSelfAtomicService()](js-apis-app-ability-abilityManager.md#abilitymanagerrestartselfatomicservice20), or [UIAbilityContext.restartApp()](js-apis-inner-application-uiAbilityContext.md#restartapp22) within 3 seconds after a successful call to this API, the system returns error code 16000064.
>
> If an application calls this API or [UIAbilityContext.restartApp()](js-apis-inner-application-uiAbilityContext.md#restartapp22) within 3 seconds after a successful call to this API, the system returns error code 16000064.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**
| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | Want parameter, which carries the information about the UIAbility to start. The system only verifies the validity of the abilityName field, and does not verify the bundleName field. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000063 | The target to restart does not belong to the current application or is not a UIAbility. |
| 16000064 | Restart too frequently. Try again at least 3s later. |

**Example**

```ts
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
              // Restart the application and launch the specified UIAbility.
              this.context.restartApp(want);
            } catch (err) {
              hilog.error(0x0000, 'testTag', `restart failed: ${err.code}, ${err.message}`);
            }
          } else {
            hilog.error(0x0000, 'testTag', "%{public}s", 'AppContext is null');
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## ApplicationContext.getCurrentAppCloneIndex<sup>12+</sup>

getCurrentAppCloneIndex(): number

Obtains the index of the current application clone.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| number | Index of the current application clone.|

**Error codes**

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000071 | The MultiAppMode is not App_CLONE. |

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onBackground() {
    // Obtain the application context
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain the clone index of the current application
      let appCloneIndex = applicationContext.getCurrentAppCloneIndex();
    } catch (error) {
      console.error(`getCurrentAppCloneIndex fail, error: ${JSON.stringify(error)}`);
    }
  }
}
```

## ApplicationContext.setFont<sup>12+</sup>

setFont(font: string): void

Sets the font for this application. This API can be called only on the main thread.

> **NOTE**
>
> Before calling this API, ensure that the window has been created and the page corresponding to the UIAbility has been loaded (using the [loadContent](../apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) API in the [onWindowStageCreate()](js-apis-app-ability-uiAbility.md#onwindowstagecreate) lifecycle).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| font | string | Yes  | Font, which can be registered by calling [UIContext.registerFont](../apis-arkui/arkts-apis-uicontext-font.md#registerfont). |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |


**Example**

```ts
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  aboutToAppear() {
    this.getUIContext().getFont().registerFont({
      familyName: 'fontName',
      familySrc: $rawfile('font/medium.ttf')  // 'font/medium.ttf' is used only as an example. Replace it with the actual font resource file.
    });

    // Set the application to use the registered custom font.
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

## ApplicationContext.setSupportedProcessCache<sup>12+</sup>

setSupportedProcessCache(isSupported : boolean): void

Sets whether the current application's process supports resource caching, so that the cached process resources can be reused when the application is started again. This API can be called only on the main thread.

This setting applies only to the current process instance and does not affect others. If the application process instance is terminated, the previously set state will not be preserved and must be reset.

> **NOTE**
> - This API only sets the application to be ready for quick startup after caching. It does not mean that quick startup will be triggered. Other conditions must be considered to determine whether to trigger quick startup.
> - To ensure that this API is effective before the process exits, it should be called as soon as possible. You are advised to call this API within the **onCreate()** callback of the [AbilityStage](../../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md).
> - If this API is called multiple times within the same process, the outcome of the final call is used. In cases where there are multiple AbilityStage instances, to achieve the desired result, this API must be called and configured with the same value in each AbilityStage.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones and 2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Parameters**
| Name       | Type    | Mandatory| Description                      |
| ------------- | -------- | ---- | -------------------------- |
| isSupported | boolean | Yes| Whether the application's process supports resource caching. **true** if supported, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 801      | Capability not supported.|
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**Example**

```ts
import { AbilityStage, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Set the current application process to support process resource cache.
      applicationContext.setSupportedProcessCache(true);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`setSupportedProcessCache fail, code: ${code}, msg: ${message}`);
    }
  }
}
```


## ApplicationContext.setFontSizeScale<sup>13+</sup>

setFontSizeScale(fontSizeScale: number): void

Sets the scale ratio for the font size of this application. This API can be called only on the main thread.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type         | Mandatory| Description                |
| ------ | ------------- | ---- | -------------------- |
| fontSizeScale | number | Yes  | Font scale ratio. The value is a non-negative number. When the application's [fontSizeScale](../../quick-start/app-configuration-file.md#configuration) is set to **followSystem** and the value set here exceeds the value of [fontSizeMaxScale](../../quick-start/app-configuration-file.md#configuration), the value of [fontSizeMaxScale](../../quick-start/app-configuration-file.md#configuration) takes effect.|

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        return;
      }
      // Obtain the application context.
      let applicationContext = this.context.getApplicationContext();
      // Set the application font size scaling ratio.
      applicationContext.setFontSizeScale(2);
    });
  }
}
```


## ApplicationContext.getCurrentInstanceKey<sup>14+</sup>

getCurrentInstanceKey(): string

Obtains the unique instance ID of this application. This API can be called only on the main thread.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000078 is returned.

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| string | Unique instance ID of the application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000078 | The multi-instance is not supported. |

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    let currentInstanceKey = '';
    try {
      // Obtain the unique instance ID of the current application in multi-instance mode.
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

## ApplicationContext.getAllRunningInstanceKeys<sup>14+</sup>

getAllRunningInstanceKeys(): Promise\<Array\<string>>;

Obtains the unique instance IDs of all multi-instances of this application. This API uses a promise to return the result. It can be called only on the main thread.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior difference**: This API can be called normally only on PC/2-in-1 devices.

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| Promise\<Array\<string>> | Promise used to return the unique instance IDs of all multi-instances of the application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |
| 16000078 | The multi-instance is not supported. |

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain the unique instance identifiers of all multi-instance instances of the application.
      applicationContext.getAllRunningInstanceKeys();
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getAllRunningInstanceKeys fail, code: ${code}, msg: ${message}`);
    }
  }
}
```

## ApplicationContext.getAllWindowStages<sup>23+</sup>

getAllWindowStages(): Promise\<Array\<window.WindowStage>>

Obtains all WindowStage objects in the current application process. This API uses a promise to return the result. It can be called only on the main thread.

This API is used to manage multiple windows in an application that contains several UIAbility components, for example, managing the states of different WindowStage objects, or synchronizing state or data between multiple windows within the same application.

 **Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type  | Description                          |
| ------ | ------------------------------ |
| Promise\<Array\<[window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md)>> | Promise used to return all WindowStage objects in the current application process.|

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Obtain all WindowStage objects in the current process of the application.
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

## ApplicationContext.enableDelayedProcessExit

enableDelayedProcessExit(): Promise\<void>

Enables delayed exit of the current process. This API uses a Promise asynchronous callback. It can be called only on the main thread.

Normally, after the last UIAbility in an application process exits, the process exits. After this API is called, the process exits 10 seconds after the last UIAbility exits. If a new UIAbility of the process is started within the 10 seconds, the process will not exit.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.                                    |
| 16000050 | Internal error. Possible causes: Fail to connect system service. |
| 16000150 | The current process has no UIAbility, and this API cannot be called. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Enable the delayed process exit feature for the current process.
      this.context.getApplicationContext().enableDelayedProcessExit().then(() => {
        console.info('enableDelayedProcessExit succeed');
      }).catch((error: BusinessError) => {
        console.error(`enableDelayedProcessExit error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch(error) {
      console.error('enableDelayedProcessExit failed. Code=%{public}d, Message=%{public}s', error.code, error.message);
    }
  }
}
```

## ApplicationContext.disableDelayedProcessExit

disableDelayedProcessExit(): Promise\<void>

Disables the delayed process exit feature for the current process. This API uses an asynchronous callback to return the result. It can be called only from the main thread.

Calling this API cancels the effect of [ApplicationContext.enableDelayedProcessExit](#applicationcontextenabledelayedprocessexit).

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.                                    |
| 16000050 | Internal error. Possible causes: Fail to connect system service. |
| 16000150 | The current process has no UIAbility, and this API cannot be called. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Disable the delayed process exit feature for the current process.
      this.context.getApplicationContext().disableDelayedProcessExit().then(() => {
        console.info('disableDelayedProcessExit succeed');
      }).catch((error: BusinessError) => {
        console.error(`disableDelayedProcessExit error, code: ${error.code}, error msg: ${error.message}`);
      });
    } catch(error) {
      console.error('disableDelayedProcessExit failed. Code=%{public}d, Message=%{public}s', error.code, error.message);
    }
  }
}
```

## ApplicationContext.startSelfUIAbility

startSelfUIAbility(want: Want): Promise\<void>

During the delayed exit of the current process, starts a UIAbility of the current process. After the UIAbility is started successfully, the current process no longer exits.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type                                | Mandatory | Description                                        |
| ---- | ----------------------------------- | --------- | -------------------------------------------------- |
| want | [Want](js-apis-app-ability-want.md) | Yes       | Want type parameter, which carries the information about the UIAbility to start. |

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.                                    |
| 16000001 | The specified ability does not exist.                        |
| 16000008 | The crowdtesting application expires.                        |
| 16000009 | An ability cannot be started or stopped in Wukong mode.      |
| 16000050 | Internal error. Possible causes: Fail to connect system service. |
| 16000122 | The target component is blocked by the system module and does not support startup. |
| 16000123 | Implicit startup is not supported.                           |
| 16000124 | Starting a remote UIAbility is not supported.                |
| 16000125 | Starting a plugin UIAbility is not supported.                |
| 16000130 | The UIAbility does not belong to the caller.                 |
| 16000161 | Delayed process exit is not pending in the current process, and this API cannot be called. |
| 16000162 | The current process still has another UIAbility, and this API cannot be called. |

**Example**

```ts
import { common, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State message: string = 'Delayed startup';
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Button(this.message)
      .fontSize(50)
      .align(Alignment.Center)
      .onClick(() => {
        try {
          const newWant: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
              'pageName': 'IndexNew'  // Mark the main page to be started.
            }
          };
          // Obtain the application context.
          let applicationContext = this.context.getApplicationContext();
          // Start the main UI during delayed exit.
          this.context.terminateSelf().then(() => {
            // Set a delay of 2000 ms to ensure that the main application has fully exited before calling the startSelfUIAbility API.
            setTimeout(() => {
              applicationContext.getApplicationContext().startSelfUIAbility(newWant).then(() => {
                hilog.info(0x0000, 'testTag', 'Main UI started successfully.');
              }).catch((error: BusinessError) => {
                hilog.error(0x0000, 'testTag', `Failed to start the main UI, code: ${error.code}, error msg: ${error.message}`);
              });
            }, 2000);
          });
        } catch (error) {
          hilog.error(0x0000, 'testTag', `Failed to start the main UI, code: ${error.code}, error msg: ${error.message}`);
        }
      });
  }
}
```

## ApplicationContext.getUIAbilityByInstanceId

getUIAbilityByInstanceId(instanceId: string): UIAbility

Obtains a specific UIAbility instance by instance ID in a multi-instance scenario. This API can be called only from the main thread.

**Since:** 26.0.0

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| instanceId | string | Yes | Instance ID of the UIAbility. |

**Return value**

| Type | Description |
| -------- | -------- |
| [UIAbility](js-apis-app-ability-uiAbility.md) | UIAbility instance corresponding to instanceId. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000003 | The id does not exist. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. System service failed to communicate with dependency module. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      let instanceId = 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx';
      // Obtain the UIAbility instance by instance ID.
      let uiAbility = applicationContext.getUIAbilityByInstanceId(instanceId);
      console.info(`getUIAbilityByInstanceId succeed, ability: ${uiAbility}`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`getUIAbilityByInstanceId fail, code: ${code}, message: ${message}`);
    }
  }
}
```
