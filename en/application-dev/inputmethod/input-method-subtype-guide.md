# Setting Input Method Subtypes
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

The input method subtypes allow the input method to switch to a specific mode or language, for example, the Chinese or English keyboard.

## Configuring and Implementing an Input Method Subtype

1. Implement an **InputMethodExtensionAbility** instance for an input method, which will be shared by all subtypes of the input method. Add **metadata** with the name **ohos_extension.input_method** to the [module.json5](../quick-start/module-configuration-file.md) file to configure resource information for all subtypes.
   ```ts
   {
     "module": {
       // ...
       "extensionAbilities": [
         {
           "description": "InputMethodExtDemo",
           "icon": "$media:icon",
           "name": "InputMethodExtAbility",
           "srcEntry": "./ets/InputMethodExtensionAbility/InputMethodService.ts",
           "type": "inputMethod",
           "exported": true,
           "metadata": [
             {
               "name": "ohos.extension.input_method",
               "resource": "$profile:input_method_config"
             }
           ]
         }
       ]
     }
   }
   ```
   
2. Configure the subtype information based on the configuration file format and fields, and place the subtype configuration file `input_method_config.json` in the **profile** folder under the application's resource directory. For details about the fields, see [InputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod-subtype.md#inputmethodsubtype). For details about how to configure the **locale** field, see [i18n-locale-culture](.././internationalization/i18n-locale-culture.md#how-it-works).
   ```
   {
     "subtypes": [
       {
         "icon": "$media:icon",
         "id": "InputMethodExtAbility",
         "label": "$string:english",
         "locale": "en-US",
         "mode": "lower"
       },
       {
         "icon": "$media:icon",
         "id": "InputMethodExtAbility1",
         "label": "$string:chinese",
         "locale": "zh-CN",
         "mode": "lower"
       }
     ]
   }
   ```
   
3. Register a listener in the input method application for subtype changes, so as to load a subtype-specific soft keyboard UI. You can also use a state variable to change the soft keyboard layout.

   ```ts
   import { InputMethodSubtype, inputMethodEngine } from '@kit.IMEKit';

   let panelInfo: inputMethodEngine.PanelInfo = {
     type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
     flag: inputMethodEngine.PanelFlag.FLG_FIXED
   };
   let inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
   // CreatePanel needs to be completed in the Create lifecycle of InputMethodExtensionAbility. this.context is InputMethodExtensionContext in InputMethodExtensionAbility.
   inputMethodAbility.createPanel(this.context, panelInfo).then(async (panel: inputMethodEngine.Panel) => {
     let inputPanel: inputMethodEngine.Panel = panel;
     inputMethodAbility.on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
       // Save the current input method subtype. You can also change the state variable value here, based on which different layouts are displayed.
       let subType: InputMethodSubtype = inputMethodSubtype;
       if (inputMethodSubtype.id == 'InputMethodExtAbility') {// Different soft keyboard UIs are loaded according to the subtype.
         inputPanel.setUiContent('pages/Index');
       }
       if (inputMethodSubtype.id == 'InputMethodExtAbility1') { // Different soft keyboard UIs are loaded according to the subtype.
         inputPanel.setUiContent('pages/Index1');
       }
     });
   }).catch((err: BusinessError) => {
     console.error(`Failed to createPanel, code: ${err.code}, message: ${err.message}`);
   });
   ```

## Obtaining Information About Input Method Subtypes

1. To obtain the current subtype of the current input method, call [getCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodgetcurrentinputmethodsubtype9).

2. To obtain all subtypes of the current input method, call [listCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#listcurrentinputmethodsubtype9).

3. To obtain all subtypes of a specified input method, call [listInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#listinputmethodsubtype9).


## Switching Between Input Method Subtypes

1. To switch to another subtype of the current input method, call [switchCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodsubtype9).

2. To switch to a specified subtype of a specified input method, call [switchCurrentInputMethodAndSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodandsubtype9).
