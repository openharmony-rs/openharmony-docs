# @ohos.InputMethodExtensionContext(InputMethodExtensionContext)

## Usage

Before using the **InputMethodExtensionContext** module, you must define a child class that inherits from  
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
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c.md) | The **InputMethodExtensionContext** module, inherited from **ExtensionContext**, provides context for **InputMethodExtension** abilities. You can use the APIs of this module to start, terminate, connect, and disconnect abilities.<br> <br> |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [InputMethodExtensionContext](arkts-ime-inputmethodextensioncontext-c-sys.md) | The **InputMethodExtensionContext** module, inherited from **ExtensionContext**, provides context for **InputMethodExtension** abilities. You can use the APIs of this module to start, terminate, connect, and disconnect abilities.<br> <br> |
<!--DelEnd-->
