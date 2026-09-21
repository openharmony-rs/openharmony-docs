# getSystemInputMethodConfigAbility

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getSystemInputMethodConfigAbility

```TypeScript
function getSystemInputMethodConfigAbility(): ElementName
```

Obtains the information about the input method configuration page ability.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Element name of the input method configuration page ability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';

let inputMethodConfig: bundleManager.ElementName = inputMethod.getSystemInputMethodConfigAbility();
```
