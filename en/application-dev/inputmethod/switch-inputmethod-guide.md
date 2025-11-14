# Switching Between Input Methods
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

You can use the APIs of the input method framework service to easily switch between input methods and input method subtypes.

> **NOTE**
>
> - The following APIs can be called only in the current input method application.
>
> - This example assumes that an input method application has been executed. For details about how to implement an input method application, see [Implementing an Input Method Application](./inputmethod-application-guide.md).

## Switching Between Input Method Subtypes

1. In the input method application in use, call [switchCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodsubtype9) with the target [InputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod-subtype.md#inputmethodsubtype) to switch to another subtype of the current input method.

   ```ts
   import { InputMethodSubtype, inputMethod } from '@kit.IMEKit';
   
   export class KeyboardController {
     async switchCurrentInputMethodSubtype() {
       try {
         let subTypes: Array<InputMethodSubtype> =
           await inputMethod.getSetting().listCurrentInputMethodSubtype(); // Obtain all subtypes of the current input method.
         let currentSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype(); // Obtain the current subtype of the current input method.
         if (subTypes.length === 0) {
           return;
         }
         for (let i = 0; i < subTypes.length; i++) {
           if (subTypes[i].id != currentSubType.id) { // If the current subtype is not the specified one, switch to the specified one. You can enter a fixed subtype as required.
             await inputMethod.switchCurrentInputMethodSubtype(subTypes[i]);
             return;
           }
         }
       } catch (err) {
         let error: BusinessError = err as BusinessError;
         console.error(`Failed to switchCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
       }
     }
   }
   ```

2. Register a listener in the input method application for subtype changes, so as to load a subtype-specific soft keyboard UI.

   ```ts
   import { InputMethodSubtype, inputMethodEngine, inputMethod } from '@kit.IMEKit';
   
   export class KeyboardController {
     async switchCurrentInputMethodSubtype() {
       let panel: inputMethodEngine.Panel; // The panel can be used only after a panel instance is created through the createPanel API.
       let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
       // Register a listener in the input method application for subtype changes.
       inputMethodAbility.on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
         if(inputMethodSubtype.id == 'InputMethodExtAbility') {
           panel.setUiContent('pages/Index'); // Assume that the panel has been created in the onCreate process in the input method application.
         }
         if(inputMethodSubtype.id == 'InputMethodExtAbility1') {
           panel.setUiContent('pages/Index1'); // Assume that the panel has been created in the onCreate process in the input method application.
         }
       });
     }
   }
   ```

## Switching Between Input Methods

In the input method application in use, call [switchInputMethod](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchinputmethod9) with the target [InputMethodProperty](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodproperty8) to switch to another input method.

```ts
import { inputMethod } from '@kit.IMEKit';

export class KeyboardController {
  async switchInputMethod(){
    try {
      let inputMethods: Array<inputMethod.InputMethodProperty> =
        await inputMethod.getSetting().getInputMethods(true); // Obtain the list of enabled input methods.
      let currentInputMethod: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod(); // Obtain the current input method.
      for (let i = 0; i < inputMethods.length; i++) {
        if (inputMethods[i].name != currentInputMethod.name) { // If the current input method is not the specified one, switch to the specified one. You can enter a fixed input method as required.
          await inputMethod.switchInputMethod(inputMethods[i]);
          return;
        }
      }
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
    }
  }
}
```

## Switching Between Input Methods and Subtypes

In the input method application in use, call [switchCurrentInputMethodAndSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodandsubtype9) with the target [InputMethodProperty](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodproperty8) and [InputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod-subtype.md#inputmethodsubtype) to switch to the specified subtype of another input method.

```ts
import { inputMethod } from '@kit.IMEKit';

export class KeyboardController {
  async switchInputMethodAndSubtype() {
    try {
      let inputMethods: Array<inputMethod.InputMethodProperty> =
        await inputMethod.getSetting().getInputMethods(true); // Obtain the list of enabled input methods.
      let currentInputMethod: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod(); // Obtain the current input method.
      for (let i = 0; i < inputMethods.length; i++) {
        if (inputMethods[i].name != currentInputMethod.name) { // If the current input method is not the specified one, switch to the specified one. You can enter a fixed input method as required.
          let subTypes = await inputMethod.getSetting().listInputMethodSubtype(inputMethods[i]); // Obtain the subtypes of the target input method.
          if (subTypes.length > 0) {
            await inputMethod.switchCurrentInputMethodAndSubtype(inputMethods[i], subTypes[0]); // This example switches to the first obtained subtype.
          }
          return;
        }
      }
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
    }
  }
}
```
