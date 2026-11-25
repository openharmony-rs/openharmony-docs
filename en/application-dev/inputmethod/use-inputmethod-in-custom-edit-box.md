# Using the Input Method in a Custom Edit Box

<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=515075d2eda02a274c0d8d0743602acd4ec711a3 translatedAt=2026-11-05T01:00:48.375Z pushedAt=2026-08-15T08:41:10.952Z nl=2 -->

In the inputmethod framework, use [getController](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodgetcontroller9) to obtain the [InputMethodController](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodcontroller) instance for binding the input method and listening to various events of the input method application, such as insertion, deletion, selection, and cursor movement. In this way, the input method can be used in the custom edit box, implementing more flexible and free editing operations.

## How to Develop

1. In your project in DevEco Studio, create an .ets file and name it the name of the target custom component, for example, **CustomInput**. Define a custom component in the file, and import **inputMethod** from @kit.IMEKit.

   ```ets
   import { inputMethod } from '@kit.IMEKit';
   
   @Component
   export struct CustomInput {
     build() {
     }
   }
   ```

2. In the component, use the **Text** component to show the text in the custom edit box, and the **inputText** state variable to specify the text to display in the text input box.

   <!-- @[input_case_input_CustomInputText](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/components/CustomInput.ets) -->

   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   import { inputMethod } from '@kit.IMEKit';
   import Log from '../model/Log';
   
   const TAG = '[Submenu]';
   
   @Component
   export struct CustomInput {
     @State inputText: string = ''; // inputText is the content to be displayed by the Text component.
     private isAttach: boolean = false;
     private inputController: inputMethod.InputMethodController = inputMethod.getController();
   
     build() {
       Text(this.inputText) // Use the Text component to show the text in the custom edit box.
         .fontSize(16)
         .width('100%')
         .lineHeight(40)
         .id('customInput')
         .height(45)
         .border({ color: '#554455', radius: 30, width: 1 })
         .maxLines(1)
         .onBlur(() => {
           this.off();
         })
         .onClick(() => {
           this.attachAndListener(); // Click the component.
         })
     }
   ```

3. In the component, obtain an **InputMethodController** instance. When the text is tapped, call the **controller** instance's **attach** method to bind and activate the soft keyboard, and  register listeners for input method events such as text insertion and deletion. This example only demonstrates insertion and deletion.

   > **NOTE**
   >
   > On PCs/2-in-1 devices and tablets, custom text boxes insert text by listening for input method insertText events, but cannot consume physical numeric key events, so digits cannot be inserted. You can enable physical numeric keyboard input for custom text boxes. For details, see [Configuring Physical Numeric Keyboard Input for Custom Text Boxes](#configuring-physical-numeric-keyboard-input-for-custom-text-boxes).

   <!-- @[input_case_input_CustomInput](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/components/CustomInput.ets) -->

   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   import { inputMethod } from '@kit.IMEKit';
   import Log from '../model/Log';
   
   const TAG = '[Submenu]';
   
   @Component
   export struct CustomInput {
     @State inputText: string = ''; // inputText is the content to be displayed by the Text component.
     private isAttach: boolean = false;
     private inputController: inputMethod.InputMethodController = inputMethod.getController();
   
     build() {
       Text(this.inputText) // Use the Text component to show the text in the custom edit box.
         .fontSize(16)
         .width('100%')
         .lineHeight(40)
         .id('customInput')
         .height(45)
         .border({ color: '#554455', radius: 30, width: 1 })
         .maxLines(1)
         .onBlur(() => {
           this.off();
         })
         .onClick(() => {
           this.attachAndListener(); // Click the component.
         })
     }
     async attachAndListener() { // Bind and set a listener.
       focusControl.requestFocus('customInput');
       try {
         await this.inputController.attach(true, {
           inputAttribute: {
             textInputType: inputMethod.TextInputType.TEXT,
             enterKeyType: inputMethod.EnterKeyType.SEARCH
           }
         });
         if (!this.isAttach) {
           this.inputController.on('insertText', (text) => {
             this.inputText += text;
           })
           this.inputController.on('deleteLeft', (length) => {
             this.inputText = this.inputText.substring(0, this.inputText.length - length);
           })
           this.isAttach = true;
         }
       } catch (err) {
         let error = err as BusinessError;
         Log.showError(TAG, `attach catch error: ${error.code} ${error.message}`);
       }
     }
   
     off() {
       this.isAttach = false;
       this.inputController.off('insertText');
       this.inputController.off('deleteLeft');
     }
   }
   ```

4. Import the component to the application UI layout. In this example, the **Index.ets** and **CustomInput.ets** files are in the same directory.

   <!-- @[input_case_input_CustomInput](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/KikaInputMethod/entry/src/main/ets/pages/PrivatePreview.ets) -->

   ``` TypeScript
   CustomInput()
   ```

## Configuring Physical Numeric Keyboard Input for Custom Text Boxes

Since API version 26.0.1, the input method framework supports physical numeric keyboard input in CustomInput (custom text box) scenarios on PCs/2-in-1 devices and tablets. Without this capability, physical numeric key events cannot be consumed and digits cannot be inserted, for example, on a verification code input screen. You can enable or disable this capability through a configuration file.

> **NOTE**
>
> This configuration takes effect only on PCs/2-in-1 devices and tablets.
> <!--RP1--><!--RP1End-->

### Configuration Steps

1. Add a configuration file.

   Create a configuration file named `easy_go.json` in the application's `entry/src/main/resources/base/profile` directory. This file name is an example; you can choose another name. Add the `easyGo` field to [module.json5](../quick-start/module-configuration-file.md) and point it to this configuration file.

   ![easy_go](./figures/easy_go.png)

2. Add the physical numeric key conversion configuration.

   Configure the properties for physical numeric keyboard input in custom text boxes in `easy_go.json`.

### Configuration Details

`easy_go.json` is a standard Object-type JSON file with two levels. The first level configures device types, and the second configures physical numeric key conversion options for each device type.

1. Device types

   The first level configures how custom text boxes receive physical numeric keyboard input on different device types.

   ```json
   { 
     "common": {},
     "phone": {},
     "2in1": {},
     "tablet": {}
   }
   ```

   | Value | Description | Optional |
   | --- | --- | --- |
   | common | Common configuration that provides base defaults for all device types. | No |
   | phone | Configuration for phones. When specified, the common configuration no longer takes effect on phones. | Yes |
   | 2in1 | Configuration for PCs/2-in-1 devices. When specified, the common configuration no longer takes effect on these devices. | Yes |
   | tablet | Configuration for tablets. When specified, the common configuration no longer takes effect on tablets. | Yes |

2. Numeric key options

   The second-level `numKeyOptions` field configures physical numeric keyboard input in custom text boxes. Its fields are described below.

   | Field | Description | Optional |
   | --- | --- | --- |
   | autoConsumeNumKeysAndInsert | Whether to receive physical numeric keyboard input. The value true enables this capability for custom text boxes; false disables it. | No |

3. Configuration examples

   > **NOTE**
   >
   > `autoConsumeNumKeysAndInsert` is mandatory and must be specified when configuring `numKeyOptions`.

   The following example enables physical numeric keyboard input for custom text boxes on PCs/2-in-1 devices:

   ```json
   {
     "common": {},
     "2in1": {
       "numKeyOptions": {
         "autoConsumeNumKeysAndInsert": true
       }
     }
   }
   ```

   The following example disables physical numeric keyboard input for custom text boxes on tablets:

   ```json
   {
     "common": {},
     "tablet": {
       "numKeyOptions": {
         "autoConsumeNumKeysAndInsert": false
       }
     }
   }
   ```


## Effect

  ![Example effect](./figures/image-1.png)