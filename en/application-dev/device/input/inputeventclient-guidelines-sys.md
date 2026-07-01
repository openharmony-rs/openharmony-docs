# Event Injection Development (for System Applications Only)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=deff468b8adbfa4199da5cbe7b6cbc33f2bddb1e translatedAt=2026-06-24T07:40:46.457Z pushedAt=2026-06-25T06:57:33.673Z -->

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