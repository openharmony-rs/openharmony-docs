# InputMethodExtensionAbility

```TypeScript
declare class InputMethodExtensionAbility
```

The **InputMethodExtensionAbility** module provides APIs for developing input methods and managing the lifecycle of input method extensions. <br> <br>  
> **NOTE:** <br>
> <br>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version. The APIs of this module can be used only in the stage model.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtensionAbility } from '@kit.IMEKit';
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Called when the **InputMethodExtensionAbility** is started to implement initialization.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information related to the **InputMethodExtensionAbility**, including the ability name and bundle name. |

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

Called when this **InputMethodExtensionAbility** is destroyed to clear resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

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

Context of the **InputMethodExtension**, which is inherited from **ExtensionContext**.

**Type:** [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework
