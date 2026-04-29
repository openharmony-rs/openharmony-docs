# 输入事件模拟开发指导

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

输入事件模拟提供键盘和鼠标操作模拟功能。使用场景例如：自动化测试、远程控制、辅助功能等需要程序化控制输入设备的场景。

## 导入模块

```js
import { inputEventClient } from '@kit.InputKit';
```

## 接口说明

输入事件模拟常用接口如下表所示，接口详细介绍请参考[@ohos.multimodalInput.inputEventClient (输入事件注入)](../../reference/apis-input-kit/js-apis-inputeventclient.md)。

| 接口名称  | 描述 |
| -------------------------------------------- | -------------------------- |
| createKeyboardController(): Promise&lt;KeyboardController&gt; |创建键盘控制器,用于模拟按键操作。|
| createMouseController(): Promise&lt;MouseController&gt; |创建鼠标控制器,用于模拟鼠标操作。|

## 使用KeyboardController

KeyboardController接口提供了一种简化的方式来模拟按键操作。它自动管理按键状态,并确保按键按下和释放事件的正确顺序。

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            // 创建键盘控制器
            let keyboardController = await inputEventClient.createKeyboardController();

            // 模拟按下和释放'A'键
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            await keyboardController.releaseKey(KeyCode.KEYCODE_A);

            // 模拟组合键(Ctrl+C)
            await keyboardController.pressKey(KeyCode.KEYCODE_CTRL_LEFT);
            await keyboardController.pressKey(KeyCode.KEYCODE_C);
            await keyboardController.releaseKey(KeyCode.KEYCODE_C);
            await keyboardController.releaseKey(KeyCode.KEYCODE_CTRL_LEFT);

            console.log('按键操作完成');
          } catch (error) {
            console.error(`按键操作失败, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

## 使用MouseController

MouseController接口提供了模拟鼠标操作的功能,包括光标移动、按键按下和轴事件(如滚动)。

```js
import { inputEventClient, Button, Axis as MouseAxis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            // 创建鼠标控制器
            let mouseController = await inputEventClient.createMouseController();

            // 将光标移动到显示器0的位置(100, 200)
            await mouseController.moveTo(0, 100, 200);

            // 模拟左键点击
            await mouseController.pressButton(Button.LEFT);
            await mouseController.releaseButton(Button.LEFT);

            // 模拟垂直滚动
            await mouseController.beginAxis(MouseAxis.SCROLL_VERTICAL, 10);
            await mouseController.updateAxis(MouseAxis.SCROLL_VERTICAL, 20);
            await mouseController.updateAxis(MouseAxis.SCROLL_VERTICAL, 30);
            await mouseController.endAxis(MouseAxis.SCROLL_VERTICAL);

            console.log('鼠标操作完成');
          } catch (error) {
            console.error(`鼠标操作失败, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```
