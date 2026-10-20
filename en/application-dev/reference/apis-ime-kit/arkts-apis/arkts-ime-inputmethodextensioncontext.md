# @ohos.InputMethodExtensionContext(InputMethodExtensionContext)

## Usage

<br><br>Before using the **InputMethodExtensionContext** module, you must define a child class that inherits from  
 **InputMethodExtensionAbility**.<br><br>```ts
 <br>import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
 <br>import { Want } from '@kit.AbilityKit';
 <br>class InputMethodExtAbility extends InputMethodExtensionAbility {
 <br> onCreate(want: Want): void {
 <br> console.info('onCreate, want:' + want.abilityName);
 <br> }
 <br>}
 <br>```

## Modules to Import

```TypeScript
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md) | The **@ohos.InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**, inherited from **ExtensionContext**, and provides context-level operation APIs for input method extension capabilities. <br> <br>This module is the context class of the input method **ExtensionAbility**, inherited from **ExtensionContext**, and is provided as the **context** property of an **InputMethodExtensionAbility** instance. It carries the context capabilities that an input method extension app can use during its lifecycle, including destroying itself and starting other apps. <br> <br>This module provides two core capabilities: (1) destroying the input method ExtensionAbility through **destroy()** to terminate the lifecycle of the input method app; (2) starting the target app through **startAbility()** so that the input method app can launch other abilities for interaction, expanding the flexibility and extensibility of input method features. <br> <br>Use this module when you develop an input method ExtensionAbility and need to perform context-level operations during its lifecycle. Typical scenarios include: the input method app actively destroys itself in the **onDestroy** callback, and the input method app needs to start the settings page or other auxiliary apps. <br> <br>The core APIs in this module are divided into two categories by feature: <br> <br>1. Lifecycle management: **destroy()** is used to destroy the input method ExtensionAbility and terminate the input method app. 2. Ability interaction: **startAbility()** is used to start a target ability (such as a settings page) from the input method app, extending the interaction between the input method app and other apps. <br> <br>Typical usage process: obtain **this.context** in the **onCreate** callback of **InputMethodExtensionAbility** → call **context.destroy()** when the input method needs to be terminated → call **context.startAbility(want)** when another app needs to be started. <br> Name &#124; Description &#124; |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c-sys.md) | The **@ohos.InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**, inherited from **ExtensionContext**, and provides context-level operation APIs for input method extension capabilities. <br> <br>This module is the context class of the input method **ExtensionAbility**, inherited from **ExtensionContext**, and is provided as the **context** property of an **InputMethodExtensionAbility** instance. It carries the context capabilities that an input method extension app can use during its lifecycle, including destroying itself and starting other apps. <br> <br>This module provides two core capabilities: (1) destroying the input method ExtensionAbility through **destroy()** to terminate the lifecycle of the input method app; (2) starting the target app through **startAbility()** so that the input method app can launch other abilities for interaction, expanding the flexibility and extensibility of input method features. <br> <br>Use this module when you develop an input method ExtensionAbility and need to perform context-level operations during its lifecycle. Typical scenarios include: the input method app actively destroys itself in the **onDestroy** callback, and the input method app needs to start the settings page or other auxiliary apps. <br> <br>The core APIs in this module are divided into two categories by feature: <br> <br>1. Lifecycle management: **destroy()** is used to destroy the input method ExtensionAbility and terminate the input method app. 2. Ability interaction: **startAbility()** is used to start a target ability (such as a settings page) from the input method app, extending the interaction between the input method app and other apps. <br> <br>Typical usage process: obtain **this.context** in the **onCreate** callback of **InputMethodExtensionAbility** → call **context.destroy()** when the input method needs to be terminated → call **context.startAbility(want)** when another app needs to be started. <br> Name &#124; Description &#124; |
<!--DelEnd-->
