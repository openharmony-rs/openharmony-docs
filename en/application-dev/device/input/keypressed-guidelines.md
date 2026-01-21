# Preferential Response of System Function Keys

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

Each system function key has a default function, which is fixedly implemented by the system. For example, the volume keys are used to adjust the device volume. However, some applications expect to customize the functions of these keys in specific scenarios. This guide is intended to support such applications in fulfilling these requirements.<br>Typical use cases: Reading applications expect to turn pages via volume keys, camera applications expect to take photos via volume keys, etc.<br>Supported function keys: Volume up and volume down keys are supported since API version 16. The multimedia-specific **Play/Pause**, **Next**, and **Previous** keys are supported since API version 21.

## Constraints

- The preferential response takes effect only when the application is in focus.
- After an application selects specific system function keys to take precedence over the system's default response, the keys' default behavior is disabled. Therefore, the application must ensure the custom function is activated only when it intends to respond.

## Available APIs

The following table lists the APIs related to key press event listening. For details about the APIs, see [ohos.multimodalInput.inputConsumer](../../reference/apis-input-kit/js-apis-inputconsumer.md).

| API | Description|
| ------------------------------------------------------------ | -------------------------- |
| on(type: "keyPressed", options: KeyPressedConfig, callback: Callback\<KeyEvent>): void |Subscribes to press events of the specified key and intercepts the default system response. |
| off(type: "keyPressed", callback?: Callback\<KeyEvent>): void |Unsubscribes from press events of the specified key and restores the default system response. |

## How to Develop

When an application is started, call [on](../../reference/apis-input-kit/js-apis-inputconsumer.md#inputconsumeronkeypressed16) to subscribe to key press events. When the application is closed, call [off](../../reference/apis-input-kit/js-apis-inputconsumer.md#inputconsumeroffkeypressed16) to unsubscribe from key press events.

### Page Turning and In-App Photographing via the Volume Button

In e-book or news reading apps, users can navigate pages via volume buttons—typically, the volume-up button turns to the next page, while the volume-down button returns to the previous page. In camera or barcode scanning apps, pressing a volume button triggers instant photography without switching to the system's camera interface.

<!-- @[input_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputKit/ArkTSInputConsumer/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { inputConsumer, KeyEvent } from '@kit.InputKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { KeyCode } from '@kit.InputKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct TestDemo14 {
  @State text: string = "Default monitoring for Volume Up and Down keys has been added."
  private volumeUpCallBackFunc: (event: KeyEvent) => void = () => {
  }
  private volumeDownCallBackFunc: (event: KeyEvent) => void = () => {
  }
  options1: inputConsumer.KeyPressedConfig = {
    key: KeyCode.KEYCODE_VOLUME_UP,
    action: 1, // The value 1 indicates a key press.
    isRepeat: false, // Key events are consumed preferentially and not reported.
  }
  options2: inputConsumer.KeyPressedConfig = {
    key: KeyCode.KEYCODE_VOLUME_DOWN,
    action: 1, // The value 1 indicates a key press.
    isRepeat: false, // Key events are consumed preferentially and not reported.
  }

  aboutToAppear(): void {
    try {
      // Callback invoked when the Volume Up button is pressed
      this.volumeUpCallBackFunc = (event: KeyEvent) => {
        this.getUIContext().getPromptAction().showToast({ message: 'Volume Up key pressed' })
        // do something
      }

      // Callback invoked when the Volume Down button is pressed
      this.volumeDownCallBackFunc = (event: KeyEvent) => {
        this.getUIContext().getPromptAction().showToast({ message: 'Volume Down key pressed' })
        // do something
      }
      // Register an event listener.
      inputConsumer.on('keyPressed', this.options1, this.volumeUpCallBackFunc);
      inputConsumer.on('keyPressed', this.options2, this.volumeDownCallBackFunc);
    } catch (error) {
      hilog.error(DOMAIN, 'InputConsumer', `Subscribe execute failed, error: %{public}s`,
        JSON.stringify(error, ["code", "message"]));
    }
  }

  build() {
    Column() {
      Row() {
        Button('Add monitoring for Volume Up key')
          .onClick(() => {
            try {
              // Add a specified callback function.
              inputConsumer.on('keyPressed', this.options1, this.volumeUpCallBackFunc);
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Successfully added monitoring for Volume Up key!' })
              this.text = "Monitoring for Volume Up key has been added."
            } catch (error) {
              hilog.error(DOMAIN, 'InputConsumer', `Unsubscribe execute failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Failed to add monitoring for Volume Up key!' })
              this.text = `Failed to add monitoring for Volume Up key: ${JSON.stringify(error, ["code", "message"])}`
            }
          })
      }.width('100%')
      .justifyContent(FlexAlign.Center)
      .margin({ top: 20, bottom: 50 })

      Row() {
        Button('Remove monitoring for Volume Up key')
          .onClick(() => {
            try {
              // Disable listening for a single callback.
              inputConsumer.off('keyPressed', this.volumeUpCallBackFunc);
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Successfully removed monitoring for Volume Up key!' })
              this.text = "Monitoring for Volume Up key has been removed."
            } catch (error) {
              hilog.error(DOMAIN, 'InputConsumer', `Unsubscribe execute failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Failed to remove monitoring for Volume Up key!' })
              this.text = `Failed to remove monitoring for Volume Up key: ${JSON.stringify(error, ["code", "message"])}`
            }
          })
      }.width('100%')
      .justifyContent(FlexAlign.Center)
      .margin({ top: 20, bottom: 50 })

      Row() {
        Button('Add monitoring for Volume Down key')
          .onClick(() => {
            try {
              // Add a specified callback function.
              inputConsumer.on('keyPressed', this.options2, this.volumeDownCallBackFunc);
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Successfully added monitoring for Volume Down key!' })
              this.text = "Monitoring for Volume Down key has been added."
            } catch (error) {
              hilog.error(DOMAIN, 'InputConsumer', `Unsubscribe execute failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Failed to add monitoring for Volume Down key!' })
              this.text = `Failed to add monitoring for Volume Down key: ${JSON.stringify(error, ["code", "message"])}`
            }
          })
      }.width('100%')
      .justifyContent(FlexAlign.Center)
      .margin({ top: 20, bottom: 50 })

      Row() {
        Button('Remove monitoring for Volume Down key')
          .onClick(() => {
            try {
              // Disable listening for a single callback.
              inputConsumer.off('keyPressed', this.volumeDownCallBackFunc);
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Successfully removed monitoring for Volume Down key!' })
              this.text = "Monitoring for Volume Down key has been removed."
            } catch (error) {
              hilog.error(DOMAIN, 'InputConsumer', `Unsubscribe execute failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
              this.getUIContext()
                .getPromptAction()
                .showToast({ message: 'Failed to remove monitoring for Volume Down key!' })
              this.text =
                `Failed to remove monitoring for Volume Down key: ${JSON.stringify(error, ["code", "message"])}`
            }
          })
      }.width('100%')
      .justifyContent(FlexAlign.Center)
      .margin({ top: 20, bottom: 50 })

      Row() {
        Text(this.text)
      }
      .width('100%')
      .justifyContent(FlexAlign.Center)
    }.width('100%').height('100%')
  }
}
```
