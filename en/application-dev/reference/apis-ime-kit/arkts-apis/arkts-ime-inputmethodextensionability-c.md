# InputMethodExtensionAbility

```TypeScript
declare class InputMethodExtensionAbility
```

The **@ohos.InputMethodExtensionAbility** module provides the base class definition for the input method ExtensionAbility. It serves as the entry point and lifecycle management framework for developing input method apps. <br> <br>As the core class module for input method ExtensionAbility, this module defines the **InputMethodExtensionAbility** class which acts as the base extension class for input method apps. You need to inherit this class and implement the **onCreate** and **onDestroy** lifecycle callbacks. The system invokes these callbacks automatically when starting or destroying the input method extension. <br> <br>This module provides two core capabilities: (1) initialization of the input method app via the **onCreate(want)** callback. This callback is invoked when the system launches the input method extension, where you complete initialization tasks such as resource loading and panel creation. (2) resource cleanup for the input method app via the **onDestroy()** callback. This callback is invoked when the system destroys the input method extension, where you release resources. In addition, the **context** property provides an **InputMethodExtensionContext** object, allowing you to perform context-level operations such as destroying the context and launching other apps during the lifecycle. <br> <br>This module is mandatory for input method app development. The workflow is as follows: inherit **InputMethodExtensionAbility** → configure ExtensionAbility information in **module.json5** → **onCreate** (initialization) is triggered upon system startup → **onDestroy** (cleanup) is triggered by system destruction or a proactive developer call to **context.destroy()**. <br> <br>  
> **NOTE:** <br>
> <br>
> `InputMethodExtensionAbility` defines only the basic lifecycle callbacks `onCreate` and `onDestroy`. The core <br>
> interaction capabilities of the input method (such as panel creation/destruction, keyboard event listening, and <br>
> client attachment) are obtained from the `InputMethodAbility` object provided by the `@ohos.inputMethodEngine` <br>
> module inside the `onCreate` callback. `onCreate` is the only entry for acquiring all key objects and creating <br>
> panels, and initialization must be completed within this callback. <br>
> <br>
> The type of the `context` property of `InputMethodExtensionAbility` is `InputMethodExtensionContext` (from the <br>
> `@ohos.InputMethodExtensionContext` module). This represents an association relationship: <br>
> `InputMethodExtensionAbility` owns the context capability of `InputMethodExtensionContext`. <br> <!-- | Name | Description |

|---|---|  
| InputMethodExtensionAbility | Base class of the input method ExtensionAbility, providing the lifecycle management framework for input method apps.Key members include: the **context** property (an **InputMethodExtensionContext** object), the **onCreate(want)** method (initialization callback), and the **onDestroy()** method (destruction callback). You need to inherit this class and override the lifecycle method. | -->

**Since:** 9

<!--Device-unnamed-declare class InputMethodExtensionAbility--><!--Device-unnamed-declare class InputMethodExtensionAbility-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Lifecycle callback invoked when the input method extension is started for initializing the input method app. <br> <br>- Meaning/Function: Initialization callback triggered when the system starts the input method ExtensionAbility. In this callback, you perform all key initialization work for the input method app, including obtaining core capability objects, creating the input method panel, and subscribing to events. <br>- Usage scenarios: Automatically triggered when the system starts the input method ExtensionAbility according to **module.json5**. This is the only entry for initializing the input method app. Acquisition of all key objects and panel creation must be completed within this callback. <br>- Use effect: After the callback finishes execution, the input method app enters the normal running state. The system subsequently triggers events such as keyboard show/hide requests and client attachment. The input method app must finish initialization (for example, subscribing to the **on('inputStart')** event and creating panels) before these events arrive; otherwise, subsequent events may not be responded to properly.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionAbility-onCreate(want: Want): void--><!--Device-InputMethodExtensionAbility-onCreate(want: Want): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want type information related to the current Extension, including the Ability name, bundle name, and so on. |

**Examples**

```TypeScript
import { InputMethodExtensionAbility, inputMethodEngine } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info(`onCreate, want: ${want.abilityName}`);

    // Obtain the input method ability object.
    let ability: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();

    // Obtain the keyboard delegate object.
    let keyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();

    // Create a panel.
    let panelInfo: inputMethodEngine.PanelInfo = {
      type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
      flag: inputMethodEngine.PanelFlag.FLG_FIXED
    };
    ability.createPanel(this.context, panelInfo, (err, panel) => {
      if (err) {
        console.error(`Failed to create panel: ${err.code}`);
        return;
      }
      console.info('Succeeded in creating panel.');
    });

    // Subscribe to the input method binding event.
    ability.on('inputStart', (kbController, inputClient) => {
      console.info('Input method bound to client.');
    });
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Lifecycle callback invoked when the input method app is destroyed for resource cleanup. <br> <br>- Meaning/Function: Cleanup callback triggered when the system destroys the input method ExtensionAbility. In this callback, you release panels, cancel event subscriptions, and perform other resource cleanup work. <br>- Usage scenarios: Automatically triggered when the system proactively destroys the input method ExtensionAbility (for example, when the system reclaims resources or the user switches to another input method) or when you proactively call **context.destroy()** to trigger destruction. Note: After the **onDestroy** callback is executed, **context** becomes unavailable, and the **context** object should not be used during or after the callback. <br>- Use effect: After the callback execution completes, the input method ExtensionAbility process is terminated, and all resources are released. Any subsequent operations will have no effect.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionAbility-onDestroy(): void--><!--Device-InputMethodExtensionAbility-onDestroy(): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Examples**

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';

class InputMethodExt extends InputMethodExtensionAbility {
  onDestroy(): void {
    // Destroy the panel, cancel event subscriptions, and perform other cleanup tasks.
    console.info('onDestroy');
  }
}
```

## context

```TypeScript
context: InputMethodExtensionContext
```

Context of the **InputMethodExtensionAbility**, inherited from **ExtensionContext**.

**Type:** [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionAbility-context: InputMethodExtensionContext--><!--Device-InputMethodExtensionAbility-context: InputMethodExtensionContext-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
