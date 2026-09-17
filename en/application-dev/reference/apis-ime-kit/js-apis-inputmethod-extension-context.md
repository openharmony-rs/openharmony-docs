# @ohos.InputMethodExtensionContext (InputMethodExtensionContext)

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c9f68a28229d3fb5da602baa0bfb8e542d407a50 translatedAt=2026-08-25T01:25:46.790Z pushedAt=2026-08-26T09:18:18.634Z -->

The **@ohos.InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**, inherited from **ExtensionContext**, and provides context-level operation APIs for input method extension capabilities.

This module is the context class of the input method **ExtensionAbility**, inherited from **ExtensionContext**, and is provided as the **context** property of an **InputMethodExtensionAbility** instance. It carries the context capabilities that an input method extension app can use during its lifecycle, including destroying itself and starting other apps.

This module provides two core capabilities: (1) destroying the input method ExtensionAbility through **destroy()** to terminate the lifecycle of the input method app; (2) starting the target app through **startAbility()** so that the input method app can launch other abilities for interaction, expanding the flexibility and extensibility of input method features.

Use this module when you develop an input method ExtensionAbility and need to perform context-level operations during its lifecycle. Typical scenarios include: the input method app actively destroys itself in the **onDestroy** callback, and the input method app needs to start the settings page or other auxiliary apps.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs of this module can be used only in the stage model.

The core APIs in this module are divided into two categories by feature:

1. Lifecycle management: **destroy()** is used to destroy the input method ExtensionAbility and terminate the input method app.

2. Ability interaction: **startAbility()** is used to start a target ability (such as a settings page) from the input method app, extending the interaction between the input method app and other apps.

Typical usage process: obtain **this.context** in the **onCreate** callback of **InputMethodExtensionAbility** → call **context.destroy()** when the input method needs to be terminated → call **context.startAbility(want)** when another app needs to be started.

| Class | Description |
|---|---|
| InputMethodExtensionContext | Input method extension context class inherited from **ExtensionContext**, which provides context‑level operation capabilities for **InputMethodExtensionAbility**. Key methods include: **destroy()** for destroying the input method itself (supports both callback‑based and promise‑based asynchronous modes), and **startAbility(want)** for starting a target app (promise‑based, added since API version 12). |

The **InputMethodExtensionContext** of this module must be obtained from a subclass instance of **InputMethodExtensionAbility**. Its APIs are used in combination with the lifecycle callbacks of **InputMethodExtensionAbility**.

```javascript
// The following is pseudocode for illustrating the calling logic.

// 1. Define an InputMethodExtensionAbility subclass.
class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want) {
    // Obtain the context object.
    let context = this.context; // InputMethodExtensionContext instance.
  }

  onDestroy() {
    // Destroy the instance in the lifecycle callback.
    this.context.destroy();
  }
}

// 2. Start the target app (for example, the input method settings page).
let targetWant = {
  bundleName: "com.example.settings",
  abilityName: "SettingsAbility"
};
this.context.startAbility(targetWant);
```

> **NOTE**
>
> The **InputMethodExtensionContext** instance is obtained through the **this.context** property of an **InputMethodExtensionAbility** subclass and cannot be created directly. **destroy()** is usually called in the **onDestroy** lifecycle callback, and you can also proactively call it at other times to terminate the input method ExtensionAbility.

## Modules to Import

```ts
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## Usage

Before using the **InputMethodExtensionContext** module, you must define a child class that inherits from **InputMethodExtensionAbility**.

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }
}
```

## InputMethodExtensionContext

**InputMethodExtensionContext** is the context of **InputMethodExtensionAbility**. It is inherited from **ExtensionContext** and provides context-level operation APIs for the input method extension ability.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

### destroy

destroy(callback: AsyncCallback&lt;void&gt;): void

Destroys this input method. This API uses an asynchronous callback to return the result.

- Meaning/Function: Destroys the current **InputMethodExtensionAbility** and terminates the running of the input method app. After the call, the system triggers the **InputMethodExtensionAbility.onDestroy()** lifecycle callback.

- Usage scenarios: Used when the input method app needs to actively terminate its own running. For example, the input method app actively exits after completing a specific task, or performs cleanup logic within the **onDestroy** callback to ensure resource release.

- Use effect: After the call succeeds, the current **InputMethodExtensionAbility** is destroyed, the system triggers the **onDestroy()** lifecycle callback, and the input method app process is terminated. Any subsequent context operations after the call will no longer take effect.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;void&gt;  | Yes   | Callback used to return the result. If the input method app is destroyed successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }

  onDestroy() {
    this.context.destroy((err: BusinessError) => {
      if (err) {
        console.error(`Failed to destroy context, err code = ${err.code}`);
        return;
      }
      console.info('Succeeded in destroying context.');
    });
  }
}
```

### destroy

destroy(): Promise&lt;void&gt;

Destroys this input method. This API uses a promise to return the result.

- Meaning/Function: Destroys the current **InputMethodExtensionAbility** and terminates the running of the input method app. After the call, the system triggers the **InputMethodExtensionAbility.onDestroy()** lifecycle callback.

- Usage scenarios: Used when the input method app needs to actively terminate its own running. It provides the same functionality and form as the callback and is suitable for scenarios that require promise chaining.

- Use effect: After the call succeeds, the current **InputMethodExtensionAbility** is destroyed, the system triggers the **onDestroy()** lifecycle callback, and the input method app process is terminated.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt;  | Promise that returns no value. |

**Example**

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }

  onDestroy() {
    this.context.destroy().then(() => {
      console.info('Succeeded in destroying context.');
    }).catch((err: BusinessError)=>{
      console.error(`Failed to destroy context, err code = ${err.code}`);
    });
  }
}
```

### startAbility<sup>12+</sup>

startAbility(want: Want): Promise&lt;void&gt;

Starts an ability. This API uses a promise to return the result.

- Meaning/Function: Starts a specified ability from the input method app, enabling the input method app to interact with other apps. The **want** parameter specifies the ability name and bundle name of the target app.

- Usage scenarios: Used when the input method app needs to launch other apps. For example, the input method app launches the system settings page for users to configure the input method, or launches a browser to open help documents.

- Use effect: After the call succeeds, the target ability is started and displayed in the foreground. The input method app itself is not affected and continues to run normally.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Want information, including the ability name and bundle name of the target application.|

Suggestions for the **want** parameter:

- Meaning/Function: Want type information that describes the target ability to start.

- Mandatory properties: **bundleName** (target app bundle name) and **abilityName** (target ability name) are mandatory; otherwise, the target ability cannot be located.

- Value range: All property values of the **want** object are of the string type and must be consistent with the **bundleName** and **abilityName** configured for the target app in **module.json5**.

- Precautions: The **bundleName** and **abilityName** in **want** must strictly match the target app's configuration (including case); otherwise, error 16000001 (the specified ability does not exist) is returned. You can obtain the correct bundle name and ability name by checking the target app's **module.json5** configuration file or using AppGallery.

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist.                   |
| 16000002 | Incorrect ability type.                                 |
| 16000004 | Cannot start an invisible component.                    |
| 16000005 | The specified process does not have the permission.     |
| 16000006 | Cross-user operations are not allowed.                  |
| 16000008 | The crowdtesting application expires.                   |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.       |
| 16000011 | The context does not exist.                             |
| 16000012 | The application is controlled.                          |
| 16000013 | The application is controlled by EDM.                   |
| 16000019 | No matching ability is found.                            |
| 16000050 | Internal error.                                         |
| 16000053 | The ability is not on the top of the UI.                |
| 16000055 | Installation-free timed out.                            |
| 16000061 | Operation not supported.                                |
| 16200001 | The caller has been released.                           |
| 16000069 | The extension cannot start the third party application. |
| 16000070 | The extension cannot start the service.                 |

**Example**

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    const context: InputMethodExtensionContext = this.context;
    const targetWant: Want = {
      bundleName: "com.example.aafwk.test",
      abilityName: "com.example.aafwk.test.TwoAbility"
    };

    context.startAbility(targetWant)
      .then(() => console.info('startAbility success'))
      .catch((err: BusinessError) => {
        console.error(`StartAbility failed. Code: ${err.code}, Message: ${err.message}`);
      });
  }

  onDestroy() {
    this.context.destroy().then(() => {
      console.info('Succeeded in destroying context.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to destroy context, err code = ${err.code}`);
    });
  }
}
```