# 优先响应系统功能键开发指导

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

每个系统功能键均具有默认功能，由系统固定实现，比如音量键是用来调节设备音量，但是部分应用在特定场景下期望定制这部分按键的功能，本篇指导用于支撑这部分应用的诉求达成。<br/>常见使用场景：阅读类型应用期望通过音量键翻页，相机应用期望通过音量键拍照等应用响应系统功能键做其他业务的场景。<br/>支持功能键列表：从API version 16开始支持音量加按键和音量减按键。从API version 21开始支持多媒体播放/暂停、多媒体下一首和多媒体上一首按键。

## 约束与限制

- 应用只有处于焦点时，优先响应才生效。
- 应用选择高于系统优先响应指定的系统功能键后，功能键的默认行为将失效，所以应用需要确保只有在确定响应时才激活该功能。

## 接口说明

按键按下事件常用接口如下表所示，接口详细介绍请参考[ohos.multimodalInput.inputConsumer文档](../../reference/apis-input-kit/js-apis-inputconsumer.md)。

| 接口名称  | 描述 |
| ------------------------------------------------------------ | -------------------------- |
| on(type: "keyPressed", options: KeyPressedConfig, callback: Callback\<KeyEvent>): void |订阅指定按键按下事件，拦截系统默认响应。  |
| off(type: "keyPressed", callback?: Callback\<KeyEvent>): void |取消按键事件订阅，恢复系统默认响应。  |

## 开发步骤

应用开启时调用[on](../../reference/apis-input-kit/js-apis-inputconsumer.md#inputconsumeronkeypressed16)方法订阅按键按下事件，应用关闭时再用[off](../../reference/apis-input-kit/js-apis-inputconsumer.md#inputconsumeroffkeypressed16)方法取消订阅按键按下事件。

### 音量键翻页和应用内拍照

在电子书或新闻阅读应用中，用户希望通过音量键控制翻页（例如：音量加键向下翻页，音量减键向上翻页）；在相机或扫码类应用中，用户按音量键可直接拍照，而不跳转系统相机应用。

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
    action: 1, // 按下按键的行为
    isRepeat: false, // 优先消费掉按键事件，不上报
  }
  options2: inputConsumer.KeyPressedConfig = {
    key: KeyCode.KEYCODE_VOLUME_DOWN,
    action: 1, // 按下按键的行为
    isRepeat: false, // 优先消费掉按键事件，不上报
  }

  aboutToAppear(): void {
    try {
      // 点击了音量按键上事件回调
      this.volumeUpCallBackFunc = (event: KeyEvent) => {
        this.getUIContext().getPromptAction().showToast({ message: 'Volume Up key pressed' })
        // do something
      }

      // 点击了音量按键下事件回调
      this.volumeDownCallBackFunc = (event: KeyEvent) => {
        this.getUIContext().getPromptAction().showToast({ message: 'Volume Down key pressed' })
        // do something
      }
      // 注册监听事件
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
              // 添加指定回调函数
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
              // 取消指定回调函数
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
              // 添加指定回调函数
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
              // 取消指定回调函数
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

