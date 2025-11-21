# Displaying Web Page Dialog Boxes
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

In HTML, JavaScript can be used to create the following types of dialog boxes: **window.alert(message)**, **window.confirm(message)**, and **window.prompt(message, defaultValue)**. These dialog boxes can be used to convey information, confirm operations, or request input from users.

Currently, ArkWeb does not provide default dialog boxes. To ensure that the dialog box of a web page can be used properly, the application needs to customize the dialog box through the [onAlert](../reference/apis-arkweb/arkts-basic-components-web-events.md#onalert), [onConfirm](../reference/apis-arkweb/arkts-basic-components-web-events.md#onconfirm), and [onPrompt](../reference/apis-arkweb/arkts-basic-components-web-events.md#onprompt9) APIs.

## Implementing the Alert Dialog Box

You can use **window.alert()** to display a dialog box that contains optional information. The alert dialog box is used to ensure that users can obtain certain information. When the alert dialog box is displayed, the user needs to click **OK** to continue the operation.
- The optional parameter **message** is a string to be displayed in the alert dialog box. If other types of values are passed, the values will be converted to strings.
- This method does not return any value.

An application can listen for the **alert** method of a web page through the [onAlert](../reference/apis-arkweb/arkts-basic-components-web-events.md#onalert) event and create a dialog box.

- Create a dialog box using [AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md).
    <!-- @[AchieveAlertDialogPage1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ShowWebPageDialog/entry/src/main/ets/pages/AchieveAlertDialogPage1.ets) -->
    
    ``` TypeScript
    import { webview } from '@kit.ArkWeb';
    import hilog from '@ohos.hilog';
    const TAG = '[Sample_ShowWebPageDialog]';
    const DOMAIN = 0xF811;
    const BUNDLE = 'ShowWebPageDialog_';
    @Entry
    @Component
    struct Index {
      @State message: string = 'Hello World';
      webviewController: webview.WebviewController = new webview.WebviewController();
      uiContext: UIContext = this.getUIContext();
      context = this.getUIContext().getHostContext();
    
      build() {
        Row() {
          Web({ src: $rawfile('test.html'), controller: this.webviewController })
            .onAlert((event) => {
              if (event) {
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.url:' + event.url);
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.message:' + event.message);
                this.uiContext.showAlertDialog({
                  // Replace $r('app.string.from') with the resource file you use.
                  title: this.context?.resourceManager.getStringSync($r('app.string.from').id) + event.url +
                    // Replace $r('app.string.warn') with the resource file you use.
                  this.context?.resourceManager.getStringSync($r('app.string.warn').id),
                  message: event.message,
                  confirm:{
                    // Replace $r('app.string.notarize') with the resource file you use.
                    value: $r('app.string.notarize'),
                    action: () => {
                      hilog.info(DOMAIN, TAG, BUNDLE, 'Alert confirmed.');
                      event.result.handleConfirm();
                    }
                  },
                  cancel: () => {
                    event.result.handleCancel();
                  }
                })
              }
              return true;
            })
        }
      }
    }
    ```
  Loaded HTML:
  ```html
  <!-- test.html -->
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport"
            content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          button,label,input {
          margin: 5px 0;
          }
      </style>
  </head>
  <body>
  <input type="text" id="alert-message" placeholder="message for alert"><br/>
  <button onclick="handleAlert()">alert</button><br/>
  <script>
      function handleAlert() {
          let message = document.getElementById("alert-message").value;
          let result = window.alert(message ? message : 'alert');
      }
  </script>
  </body>
  </html>
  ```

- Create a dialog box using [CustomDialog-AlertDialog](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Dialog.md#alertdialog).
    <!-- @[AchieveAlertDialogPage2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ShowWebPageDialog/entry/src/main/ets/pages/AchieveAlertDialogPage2.ets) -->
    
    ``` TypeScript
    import { AlertDialog } from '@kit.ArkUI';
    import { webview } from '@kit.ArkWeb';
    import hilog from '@ohos.hilog';
    const TAG = '[Sample_ShowWebPageDialog]';
    const DOMAIN = 0xF811;
    const BUNDLE = 'ShowWebPageDialog_';
    
    @Entry
    @Component
    struct AlertDialogPage {
      @State message: string = 'Hello World';
      @State title: string = 'Hello World';
      @State subtitle: string = '';
      @State result: JsResult | null = null;
      webviewController: webview.WebviewController = new webview.WebviewController();
      dialogControllerAlert: CustomDialogController = new CustomDialogController({
        builder: AlertDialog({
          primaryTitle: this.title,
          secondaryTitle: this.subtitle,
          content: this.message,
          primaryButton: {
            // Replace $r('app.string.notarize') with the resource file you use.
            value: $r('app.string.notarize'),
            role: ButtonRole.ERROR,
            action: () => {
              hilog.info(DOMAIN, TAG, BUNDLE, 'Callback when the second button is clicked');
              this.result?.handleConfirm();
            }
          },
        }),
        onWillDismiss: () => {
          this.result?.handleCancel();
          this.dialogControllerAlert.close();
        }
      })
      context = this.getUIContext().getHostContext();
      build() {
        Column() {
          Web({ src: $rawfile('alert.html'), controller: this.webviewController })
            .onAlert((event) => {
              if (event) {
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.url:' + event.url);
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.message:' + event.message);
                // Replace $r('app.string.from') with the resource file you use.
                this.title = this.context?.resourceManager.getStringSync($r('app.string.from').id) + event.url +
                  // Replace $r('app.string.warn') with the resource file you use.
                this.context?.resourceManager.getStringSync($r('app.string.warn').id);
                this.message = event.message;
                this.result = event.result;
                this.dialogControllerAlert.open();
              }
              return true;
            })
        }
      }
    }
    ```
  Loaded HTML:
  ```html
  <!-- alert.html -->
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport"
            content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          button,label,input {
          margin: 5px 0;
          }
      </style>
  </head>
  <body>
  <input type="text" id="alert-message" placeholder="message for alert"><br/>
  <button onclick="handleAlert()">alert</button><br/>
  <script>
      function handleAlert() {
          let message = document.getElementById("alert-message").value;
          let result = window.alert(message ? message : 'alert');
      }
  </script>
  </body>
  </html>
  ```

  ![AlertDialog](./figures/web-alert-dialog.gif)

## Implementing the Confirm Dialog Box

You can use **window.confirm()** to display a dialog box that contains optional messages and waits for the user to confirm or cancel it.
- The optional parameter **message** is a string to be displayed in the dialog box. If other types of values are passed, the values will be converted to strings.
- This method returns a Boolean value, indicating whether OK (**true**) or Cancel (**false**) is selected. If the application ignores the dialog box on the page, the return value is always **false**.

The confirm dialog box is used to check whether the user accepts an operation such as leaving a web page to prevent data loss.

An application can listen for the **confirm** method of a web page through the [onConfirm](../reference/apis-arkweb/arkts-basic-components-web-events.md#onconfirm) event and create a dialog box.

- Create a dialog box using [AlertDialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md).
    <!-- @[AchieveConfirmDialogPage1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ShowWebPageDialog/entry2/src/main/ets/pages/AchieveConfirmDialogPage1.ets) -->
    
    ``` TypeScript
    import { webview } from '@kit.ArkWeb';
    import hilog from '@ohos.hilog';
    const TAG = '[Sample_ShowWebPageDialog]';
    const DOMAIN = 0xF811;
    const BUNDLE = 'ShowWebPageDialog_';
    
    @Entry
    @Component
    struct Index {
      @State message: string = 'Hello World';
      webviewController: webview.WebviewController = new webview.WebviewController();
      uiContext: UIContext = this.getUIContext();
      context = this.getUIContext().getHostContext();
      build() {
        Column() {
          Web({ src: $rawfile('test.html'), controller: this.webviewController })
            .onConfirm((event) => {
              if (event) {
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.url:' + event.url);
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.message:' + event.message);
                this.uiContext.showAlertDialog({
                  // Replace $r('app.string.from') with the resource file you use.
                  title: this.context?.resourceManager.getStringSync($r('app.string.from').id) +
                    // Replace $r('app.string.info') with the resource file you use.
                  event.url + this.context?.resourceManager.getStringSync($r('app.string.info').id),
                  message: event.message,
                  primaryButton: {
                    value: 'cancel',
                    action: () => {
                      event.result.handleCancel();
                    }
                  },
                  secondaryButton: {
                    value: 'ok',
                    action: () => {
                      event.result.handleConfirm();
                    }
                  },
                  cancel: () => {
                    event.result.handleCancel();
                  }
                })
              }
              return true;
            })
        }
      }
    }
    ```

  Loaded HTML:
  ```html
  <!-- test.html -->
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport"
            content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          button,label,input {
          margin: 5px 0;
          }
      </style>
  </head>
  <body>
  result: <label id="confirmLabel" for="confirm"></label><br/>
  <input type="text" id="confirm-message" placeholder="message for confirm"><br/>
  <button id="confirm" onclick="handleConfirm()">confirm</button><br/>
  <script>
      function handleConfirm() {
          let message = document.getElementById("confirm-message").value;
          let result = window.confirm(message ? message : 'confirm');
          console.info(result);
          document.getElementById("confirmLabel").innerHTML=String(result);
      }
  </script>
  </body>
  </html>
  ```

- Create a dialog box using [CustomDialog-ConfirmDialog](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Dialog.md#confirmdialog).
    <!-- @[AchieveConfirmDialogPage2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ShowWebPageDialog/entry2/src/main/ets/pages/AchieveConfirmDialogPage2.ets) -->

    ``` TypeScript
    import { webview } from '@kit.ArkWeb';
    import { ConfirmDialog } from '@kit.ArkUI';
    import hilog from '@ohos.hilog';
    const TAG = '[Sample_ShowWebPageDialog]';
    const DOMAIN = 0xF811;
    const BUNDLE = 'ShowWebPageDialog_';
    
    @Entry
    @Component
    struct DialogConfirmDialog {
      @State message: string = 'Hello World';
      @State title: string = 'Hello World';
      @State result: JsResult | null = null;
      context = this.getUIContext().getHostContext()
      webviewController: webview.WebviewController = new webview.WebviewController();
      isChecked = false;
      dialogControllerCheckBox: CustomDialogController = new CustomDialogController({
        builder: ConfirmDialog({
          title: this.title,
          content: this.message,
          // Selected state of the check box
          isChecked: this.isChecked,
          // Content of the check box
          // Replace $r('app.string.noPrompt') with the resource file you use.
          checkTips: $r('app.string.noPrompt'),
          primaryButton: {
            // Replace $r('app.string.no') with the resource file you use.
            value: $r('app.string.no'),
            action: () => {
              this.result?.handleCancel();
            },
          },
          secondaryButton: {
            // Replace $r('app.string.allow') with the resource file you use.
            value: $r('app.string.allow'),
            action: () => {
              this.isChecked = false;
              hilog.info(DOMAIN, TAG, BUNDLE, 'Callback when the second button is clicked');
              this.result?.handleConfirm();
            }
          },
          onCheckedChange: (checked) => {
            this.isChecked = checked;
            hilog.info(DOMAIN, TAG, BUNDLE, 'Callback when the checkbox is clicked');
          },
        }),
        onWillDismiss: () => {
          this.result?.handleCancel();
          this.dialogControllerCheckBox.close();
        },
        autoCancel: true
      })
    
      build() {
        Column() {
          Web({ src: $rawfile('confirm.html'), controller: this.webviewController })
            .onConfirm((event) => {
              if (event) {
                if (this.isChecked) {
                  event.result.handleCancel();
                } else {
                  hilog.info(DOMAIN, TAG, BUNDLE, 'event.url:' + event.url);
                  hilog.info(DOMAIN, TAG, BUNDLE, 'event.message:' + event.message);
                  // Replace $r('app.string.from') with the resource file you use.
                  this.title = this.context?.resourceManager.getStringSync($r('app.string.from').id) +
                    // Replace $r('app.string.info') with the resource file you use.
                  event.url + this.context?.resourceManager.getStringSync($r('app.string.info').id);
                  this.message = event.message;
                  this.result = event.result;
                  this.dialogControllerCheckBox.open();
                }
              }
              return true;
            })
        }
      }
    }
    ```
  Loaded HTML:
  ```html
  <!-- confirm.html -->
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport"
            content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          button,label,input {
          margin: 5px 0;
          }
      </style>
  </head>
  <body>
  result: <label id="confirmLabel" for="confirm"></label><br/>
  <input type="text" id="confirm-message" placeholder="message for confirm"><br/>
  <button id="confirm" onclick="handleConfirm()">confirm</button><br/>
  <script>
      function handleConfirm() {
          let message = document.getElementById("confirm-message").value;
          let result = window.confirm(message ? message : 'confirm');
          console.info(result);
          document.getElementById("confirmLabel").innerHTML=String(result);
      }
  </script>
  </body>
  </html>
  ```

  ![ConfirmDialog](./figures/web-confirm-dialog.gif)

## Implementing the Prompt Dialog Box

You can use **window.prompt()** to display a dialog box and wait for the user to submit text or cancel the dialog box. The user needs to input a value and then click **OK **or **Cancel**. If **OK** is clicked, the input value is returned. If **Cancel** is clicked, **null** is returned.
- The optional parameter **message** is a text displayed to the user. If no message is required, this parameter can be ignored.
- The optional parameter **defaultValue** is a string that contains the default value displayed in the text input field.
- The return value is a string of the text input by the user or **null**.

The prompt box is used to prompt users to input a value, which is usually used in scenarios where users need to input a temporary password or verification code.

An application can listen for the **prompt** method of a web page through the [onPrompt](../reference/apis-arkweb/arkts-basic-components-web-events.md#onprompt9) event and create a dialog box.

- Create a dialog box using [CustomDialog-CustomContentDialog](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Dialog.md#customcontentdialog12).
    <!-- @[AchievePromptDialogPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ShowWebPageDialog/entry/src/main/ets/pages/AchievePromptDialogPage.ets) -->
    
    ``` TypeScript
    import { CustomContentDialog } from '@kit.ArkUI';
    import { webview } from '@kit.ArkWeb';
    import hilog from '@ohos.hilog';
    const TAG = '[Sample_ShowWebPageDialog]';
    const DOMAIN = 0xF811;
    const BUNDLE = 'ShowWebPageDialog_';
    
    @Entry
    @Component
    struct PromptDialog {
      @State message: string = 'Hello World';
      @State title: string = 'Hello World';
      @State result: JsResult | null = null;
      promptResult: string = '';
      webviewController: webview.WebviewController = new webview.WebviewController();
      context = this.getUIContext().getHostContext();
      dialogController: CustomDialogController = new CustomDialogController({
        builder: CustomContentDialog({
          primaryTitle: this.title,
          contentBuilder: () => {
            this.buildContent();
          },
          buttons: [
            {
              // Replace $r('app.string.cancel') with the resource file you use.
              value: $r('app.string.cancel'),
              buttonStyle: ButtonStyleMode.TEXTUAL,
              action: () => {
                hilog.info(DOMAIN, TAG, BUNDLE, 'Callback when the button is clicked');
                this.result?.handleCancel();
              }
            },
            {
              // Replace $r('app.string.notarize') with the resource file you use.
              value: $r('app.string.notarize'),
              buttonStyle: ButtonStyleMode.TEXTUAL,
              action: () => {
                this.result?.handlePromptConfirm(this.promptResult);
              }
            }
          ],
        }),
        onWillDismiss: () => {
          this.result?.handleCancel();
          this.dialogController.close();
        }
      });
    
      // Custom content area of the dialog box
      @Builder
      buildContent(): void {
        Column() {
          Text(this.message)
          TextInput()
            .onChange((value) => {
              this.promptResult = value;
            })
            .defaultFocus(true)
        }
        .width('100%')
      }
    
      build() {
        Column() {
          Web({ src: $rawfile('prompt.html'), controller: this.webviewController })
            .onPrompt((event) => {
              if (event) {
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.url:' + event.url);
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.message:' + event.message);
                hilog.info(DOMAIN, TAG, BUNDLE, 'event.value:' + event.value);
                // Replace $r('app.string.from') with the resource file you use.
                this.title = this.context?.resourceManager.getStringSync($r('app.string.from').id) +
                  // Replace $r('app.string.info') with the resource file you use.
                event.url + this.context?.resourceManager.getStringSync($r('app.string.info').id);
                this.message = event.message;
                this.promptResult = event.value;
                this.result = event.result;
                this.dialogController.open();
              }
              return true;
            })
        }
      }
    }
    ```
  Loaded HTML:
  ```html
  <!-- prompt.html -->
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport"
            content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
      <style>
          button,label,input {
          margin: 5px 0;
          }
      </style>
  </head>
  <body>
  result: <label id="promptLabel" for="prompt"></label><br/>
  <input type="text" id="prompt-message" placeholder="message for prompt"><br/>
  <input type="text" id="prompt-value" placeholder="default value for prompt"><br/>
  <button id="prompt" onclick="handlePrompt()">prompt</button><br/>
  <script>
      function handlePrompt() {
          let message = document.getElementById("prompt-message").value;
          let defaultValue = document.getElementById("prompt-value").value;
          let result = window.prompt(message ? message : 'prompt', defaultValue);
          console.info(result);
          document.getElementById("promptLabel").innerHTML=result;
      }
  </script>
  </body>
  </html>
  ```

Required resource file **string.json**:

  ```json
  {
    "string": [
      {
        "name": "from",
        "value": "From"
      },
      {
        "name": "warn",
        "value": "Warning"
      },
      {
        "name": "notarize",
        "value": "OK"
      },
      {
        "name": "cancel",
        "value": "Cancel"
      },
      {
        "name": "info",
        "value": "Message"
      }
    ]
  }
  ```
  ![PromptDialog](./figures/web-prompt-dialog.gif)
