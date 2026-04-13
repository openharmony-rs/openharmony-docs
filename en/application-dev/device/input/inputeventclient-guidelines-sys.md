# Event Injection Development (for System Applications Only)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

The **inputEventClient** module enables an application to listen for injected input events, such as mouse click events and combination key events. For example, if you need to verify the combination key function of an application, you can listen for combination key events to serve that purpose.

## Modules to Import

```js
import { inputEventClient } from '@kit.InputKit';
```

## Available APIs

The following table lists common APIs for event injection. For details, see [@ohos.multimodalInput.inputEventClient (Input Event Injection) (System API)](../../reference/apis-input-kit/js-apis-inputeventclient-sys.md).

| API | Description|
| -------------------------------------------- | -------------------------- |
| injectEvent({KeyEvent: KeyEvent}): void |Injects keys (including single keys and combination keys).|
| injectMouseEvent(mouseEvent: MouseEventData): void |Injects a mouse/touchpad event.|
| injectTouchEvent(touchEvent: TouchEventData): void |Injects a touchscreen event.|
| createKeyboardController(): Promise&lt;KeyboardController&gt; |Creates a keyboard controller for simulating key operations.|
| createMouseController(): Promise&lt;MouseController&gt; |Creates a mouse controller for simulating mouse operations.|

## How to Develop

Assume that an application calls the Home key to return to the home screen. When the Home key is pressed, check whether [injectEvent](../../reference/apis-input-kit/js-apis-inputeventclient-sys.md#inputeventclientinjectevent) is called to inject the Home key to determine if the Home key takes effect.

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
            } // Home key pressing event.

            class EventDown {
              KeyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventDown: EventDown = { KeyEvent: backKeyDown }
            inputEventClient.injectEvent(eventDown); // Inject the Home key pressing event.

            let backKeyUp: inputEventClient.KeyEvent = {
              isPressed: false,
              keyCode: 2,
              keyDownDuration: 0,
              isIntercepted: false
            }; // Home key release event.

            class EventUp {
              KeyEvent: inputEventClient.KeyEvent | null = null
            }

            let eventUp: EventUp = { KeyEvent: backKeyUp }
            inputEventClient.injectEvent(eventUp); // Inject the Home key release event and check whether the Home key function takes effect and whether the application returns to the home screen.
          } catch (error) {
            console.error(`Failed to inject KeyEvent, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

## Using KeyboardController

The KeyboardController interface provides a simplified way to simulate key operations. It manages key state automatically and ensures proper sequencing of key press and release events.

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
            // Create a keyboard controller
            let keyboardController = await inputEventClient.createKeyboardController();

            // Simulate pressing and releasing the 'A' key
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            await keyboardController.releaseKey(KeyCode.KEYCODE_A);

            // Simulate a key combination (Ctrl+C)
            await keyboardController.pressKey(KeyCode.KEYCODE_CTRL_LEFT);
            await keyboardController.pressKey(KeyCode.KEYCODE_C);
            await keyboardController.releaseKey(KeyCode.KEYCODE_C);
            await keyboardController.releaseKey(KeyCode.KEYCODE_CTRL_LEFT);

            console.log('Key operations completed successfully');
          } catch (error) {
            console.error(`Failed to perform key operations, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

## Using MouseController

The MouseController interface provides functions for simulating mouse operations including cursor movement, button presses, and axis events (such as scrolling).

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
            // Create a mouse controller
            let mouseController = await inputEventClient.createMouseController();

            // Move cursor to position (100, 200) on display 0
            await mouseController.moveTo(0, 100, 200);

            // Simulate left button click
            await mouseController.pressButton(Button.LEFT);
            await mouseController.releaseButton(Button.LEFT);

            // Simulate vertical scroll
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 30);
            await mouseController.endAxis(Axis.VERTICAL_SCROLL);

            console.log('Mouse operations completed successfully');
          } catch (error) {
            console.error(`Failed to perform mouse operations, error: ${JSON.stringify(error, ["code", "message"])}`);
          }
        })
    }
  }
}
```

