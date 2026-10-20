# InputMethodExtensionContext

```TypeScript
declare class InputMethodExtensionContext extends ExtensionContext
```

The **@ohos.InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**, inherited from **ExtensionContext**, and provides context-level operation APIs for input method extension capabilities. <br> <br>This module is the context class of the input method **ExtensionAbility**, inherited from **ExtensionContext**, and is provided as the **context** property of an **InputMethodExtensionAbility** instance. It carries the context capabilities that an input method extension app can use during its lifecycle, including destroying itself and starting other apps. <br> <br>This module provides two core capabilities: (1) destroying the input method ExtensionAbility through **destroy()** to terminate the lifecycle of the input method app; (2) starting the target app through **startAbility()** so that the input method app can launch other abilities for interaction, expanding the flexibility and extensibility of input method features. <br> <br>Use this module when you develop an input method ExtensionAbility and need to perform context-level operations during its lifecycle. Typical scenarios include: the input method app actively destroys itself in the **onDestroy** callback, and the input method app needs to start the settings page or other auxiliary apps. <br> <br>The core APIs in this module are divided into two categories by feature: <br> <br>1. Lifecycle management: **destroy()** is used to destroy the input method ExtensionAbility and terminate the input method app.
2. Ability interaction: **startAbility()** is used to start a target ability (such as a settings page) from the input method app,
extending the interaction between the input method app and other apps. <br> <br>Typical usage process: obtain **this.context** in the **onCreate** callback of **InputMethodExtensionAbility** → call **context.destroy()** when the input method needs to be terminated → call **context.startAbility(want)** when another app needs to be started. <br> Name | Description |

|---|---|  
| InputMethodExtensionContext | Input method extension context class inherited from **ExtensionContext**, which provides context‑level operation capabilities for **InputMethodExtensionAbility**. Key methods include: **destroy()** for destroying the input method itself (supports both callback‑based and promise‑based asynchronous modes), and **startAbility(want)** for starting a target app (promise‑based, added since API version 12). | <br> <br>The **InputMethodExtensionContext** of this module must be obtained from a child class instance of **InputMethodExtensionAbility**. Its APIs are used in combination with the lifecycle callbacks of **InputMethodExtensionAbility**. <br> <br>  
> **NOTE:** <br>
> <br>
> The `InputMethodExtensionContext` instance is obtained through the `this.context` property of an <br>
> `InputMethodExtensionAbility` child class and cannot be created directly. `destroy()` is usually called in the <br>
> `onDestroy` lifecycle callback, and you can also proactively call it at other times to terminate the input method <br>
> ExtensionAbility.

**Inheritance/Implementation:** InputMethodExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 9

<!--Device-unnamed-declare class InputMethodExtensionContext extends ExtensionContext--><!--Device-unnamed-declare class InputMethodExtensionContext extends ExtensionContext-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

Destroys this input method. This API uses an asynchronous callback to return the result. <br> <br>- Meaning/Function: Destroys the current **InputMethodExtensionAbility** and terminates the running of the input method app. After the call, the system triggers the **InputMethodExtensionAbility.onDestroy()** lifecycle callback. <br>- Usage scenarios: Used when the input method app needs to actively terminate its own running. For example, the input method app actively exits after completing a specific task, or performs cleanup logic within the **onDestroy** callback to ensure resource release. <br>- Use effect: After the call succeeds, the current **InputMethodExtensionAbility** is destroyed, the system triggers the **onDestroy()** lifecycle callback, and the input method app process is terminated. Any subsequent context operations after the call will no longer take effect.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-destroy(callback: AsyncCallback<void>): void--><!--Device-InputMethodExtensionContext-destroy(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the input method app is destroyed successfully, err is undefined; otherwise, it is an error object. |

**Examples**

```TypeScript
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

## destroy

```TypeScript
destroy(): Promise<void>
```

Destroys this input method. This API uses a promise to return the result. <br> <br>- Meaning/Function: Destroys the current **InputMethodExtensionAbility** and terminates the running of the input method app. After the call, the system triggers the **InputMethodExtensionAbility.onDestroy()** lifecycle callback. <br>- Usage scenarios: Used when the input method app needs to actively terminate its own running. It provides the same functionality and form as the callback and is suitable for scenarios that require promise chaining. <br>- Use effect: After the call succeeds, the current **InputMethodExtensionAbility** is destroyed, the system triggers the **onDestroy()** lifecycle callback, and the input method app process is terminated.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-destroy(): Promise<void>--><!--Device-InputMethodExtensionContext-destroy(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
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

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

Starts an ability. This API uses a promise to return the result. <br> <br>- Meaning/Function: Starts a specified ability from the input method app, enabling the input method app to interact with other apps. The **want** parameter specifies the ability name and bundle name of the target app. <br>- Usage scenarios: Used when the input method app needs to launch other apps. For example, the input method app launches the system settings page for users to configure the input method, or launches a browser to open help documents. <br>- Use effect: After the call succeeds, the target ability is started and displayed in the foreground. The input method app itself is not affected and continues to run normally.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-startAbility(want: Want): Promise<void>--><!--Device-InputMethodExtensionContext-startAbility(want: Want): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want type information used to specify the target app, including the ability name, bundle name, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../../apis-ability-kit/errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000061](../../apis-ability-kit/errorcode-ability.md#16000061-unsupported-operation) | Operation not supported. |
| [16000069](../../apis-ability-kit/errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application. |
| [16000070](../../apis-ability-kit/errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-caller-released) | The caller has been released. |

**Examples**

```TypeScript
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
