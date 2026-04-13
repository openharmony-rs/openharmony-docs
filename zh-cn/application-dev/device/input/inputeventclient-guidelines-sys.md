# 事件注入开发指导（仅对系统应用开放）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## 场景介绍

事件注入提供注入输入事件功能，比如注入鼠标点击事件、键盘组合键等。使用场景例如：当用户需要验证应用的组合键功能时，开发者可以通过注入组合键事件判断功能是否生效。

## 导入模块

```js
import { inputEventClient } from '@kit.InputKit';
```

## 接口说明

事件注入常用接口如下表所示，接口详细介绍请参考[@ohos.multimodalInput.inputEventClient (输入事件注入)(系统接口)](../../reference/apis-input-kit/js-apis-inputeventclient-sys.md)。

| 接口名称  | 描述 |
| -------------------------------------------- | -------------------------- |
| injectEvent({KeyEvent: KeyEvent}): void |按键（包括单个按键和组合键）注入。 |
| injectMouseEvent(mouseEvent: MouseEventData): void |鼠标/触控板事件注入。 |
| injectTouchEvent(touchEvent: TouchEventData): void |触屏输入事件注入。|
| createKeyboardController(): Promise&lt;KeyboardController&gt; |创建键盘控制器,用于模拟按键操作。|
| createMouseController(): Promise&lt;MouseController&gt; |创建鼠标控制器,用于模拟鼠标操作。|


## 开发步骤

应用调用Home键返回桌面，调用[injectEvent](../../reference/apis-input-kit/js-apis-inputeventclient-sys.md#inputeventclientinjectevent)注入Home按键，查看应用中Home按键功能是否生效。

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let backKeyDown: inputEventClient.KeyEvent = {
              isPressed: true,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            } // Home按键按下事件

            class EventDown {
              KeyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventDown: EventDown = { KeyEvent: backKeyDown }
            inputEventClient.injectEvent(eventDown); // 注入Home按键按下事件

            let backKeyUp: inputEventClient.KeyEvent = {
              isPressed: false,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            }; // Home按键抬起事件

            class EventUp {
              KeyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventUp: EventUp = { KeyEvent: backKeyUp }
            inputEventClient.injectEvent(eventUp); // 注入Home按键抬起事件,查看Home键功能是否生效，应用是否返回桌面
          } catch (error) {
            console.error(`Failed to inject KeyEvent, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

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
import { inputEventClient, Button, Axis } from '@kit.InputKit';

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
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 30);
            await mouseController.endAxis(Axis.VERTICAL_SCROLL);

            console.log('鼠标操作完成');
          } catch (error) {
            console.error(`鼠标操作失败, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

