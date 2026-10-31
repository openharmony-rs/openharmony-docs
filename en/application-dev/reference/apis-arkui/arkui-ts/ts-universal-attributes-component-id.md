# Component ID
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e8a3df3f036267095aa2be3a05bfa4ba7c1727ba translatedAt=2026-09-01T12:19:40.469Z -->

**id** is the unique identifier of a component, which is unique within the entire application. This module provides APIs related to component IDs. You can obtain the attributes of a component with a specified ID, obtain the component tree and component attributes, and send events to a component with a specified ID. The preceding extended capabilities are intended for application testing purposes only.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - If multiple IDs or keys are set for the same component, the last one set takes effect.


## id

id(value: string): T

Unique identifier of a component. The uniqueness is ensured by the user. If multiple IDs are set for the same component, the last one set takes effect. If no ID is set, the component ID is empty by default. When used together with **key**, the attribute assigned later overrides the attribute assigned earlier.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory| Description                      |
| ------ | -------- | -----|---------------------- |
| value  | string   |  Yes  | Unique identifier of the component. The uniqueness is guaranteed by the user. When used together with key, the attribute assigned later overrides the attribute assigned earlier. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## key<sup>12+</sup>

key(value: string): T

Sets a unique identifier for this component, with uniqueness guaranteed by the user.

This API is used only for test purposes. When this attribute is used with **id**, the last assigned value takes effect. You are advised to set only **id**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory| Description                      |
| ------ | -------- | -----|---------------------- |
| value   | string   | Yes | Unique identifier of the component. The uniqueness is guaranteed by the user. In concurrent use with id, the attribute assigned later overrides the attribute assigned earlier. It is recommended that only id be set.<br>Default value: '' |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Return the current component, used for chained calls. |

## Component ID–Based Extended Capabilities

The component ID–based extended capabilities are designed specifically for application testing purposes. The following API examples require debugging within the application project's **ohosTest/ets/test** directory. For detailed implementation guidance, see <!--RP1-->[JsUnit User Guide](../../../../application-dev/application-test/unittest-guidelines.md)<!--RP1End-->.

### getInspectorByKey<sup>9+</sup>

getInspectorByKey(id: string): string

Obtains all attributes of the component with the specified ID, excluding the information about child components.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory    | Description       |
| ---- | -------- | ---- | -------------|
| id   | string   | Yes   | ID of the component whose attributes are to be obtained.|

**Return value**

| Type       | Description            |
| -------| -------------- |
| string | JSON string of the component attribute list.<br>**Note:**<br>The string information contains the tag and ID of the component, the position information (coordinates relative to the upper left corner of the window), and the attribute information contained in the component (for test inspection). For the meaning of each field in the component, see the return value description of [getInspectorInfo](../js-apis-arkui-frameNode.md#getinspectorinfo12). |

**Example**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .id('TEXT')
        .onClick(() => {
          console.info(`Text is clicked`);
        })
      Button('TEST BUTTON').onClick(() => {
        let result = getInspectorByKey('TEXT');
        console.info(`result is ${result}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### getInspectorTree<sup>9+</sup>

getInspectorTree(): Object

Obtains the component tree and component attributes.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                           |
| ------ | --------------------------- |
| Object | JSON object of the component tree and component attribute list. For details about each field in the component, see the return value description of [getInspectorInfo](../js-apis-arkui-frameNode.md#getinspectorinfo12).|

**Example**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .id('TEXT')
        .onClick(() => {
          console.info(`Text is clicked`);
        })
      Button('TEST BUTTON').onClick(() => {
        let result = getInspectorTree();
        console.info(`result is ${JSON.stringify(result)}`);
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### sendEventByKey<sup>9+</sup>

sendEventByKey(id: string, action: number, params: string): boolean

Sends an event to the component with the specified ID.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type     | Mandatory      | Description                        |
| ------ | -------| ---- | -------------------------- |
| id     | string | Yes   | ID of the component to which the event is to be sent.                     |
| action | number | Yes    | Type of the event to trigger. Currently supported values:<br>-&nbsp;Click event:&nbsp;10.<br>-&nbsp;LongClick event:&nbsp;11. |
| params | string | Yes    | Event parameter. The currently supported event types (Click and LongClick) require no additional parameter. Pass an empty string&nbsp;"".            |

**Return value**

| Type         | Description                        |
| -------- | --------------------------|
| boolean  | Returns **true** if the component with the specified ID is found; returns **false** otherwise.|

**Example**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .id('TEXT')
        .onClick(() => {
          console.info(`Text is clicked`);
        })
      Button('TEST BUTTON').onClick(() => {
        sendEventByKey('TEXT', 10, '');
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### sendTouchEvent<sup>9+</sup>

sendTouchEvent(event: TouchObject): boolean

Sends a touch event.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type           | Mandatory | Description                                                        |
| ----- | ----------- | ---- | ------------------------------------------------------------ |
| event | [TouchObject](ts-universal-events-touch.md#touchobject) | Yes | Touch event. For details about the event parameter, see [TouchObject](ts-universal-events-touch.md#touchobject). |

**Return value**

| Type     | Description                        |
| ------- | ---------------------------|
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise.|

### sendKeyEvent<sup>9+</sup>

sendKeyEvent(event: KeyEvent): boolean

Sends a key event.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type    | Mandatory     | Description                                                        |
| ----- | -------- | ----  | ------------------------------------------------------------ |
| event | [KeyEvent](ts-universal-events-key.md#keyevent) | Yes    | Key event. For details, see [KeyEvent](ts-universal-events-key.md#keyevent).|

**Return value**

| Type     | Description                          |
| ------- | ------------------------------|
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise.|

### sendMouseEvent<sup>9+</sup>

sendMouseEvent(event: MouseEvent): boolean

Sends a mouse event.

This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type      | Mandatory      | Description                                    |
| ----- | ---------- | ----  | --------------------------------------- |
| event | [MouseEvent](ts-universal-mouse-key.md#mouseevent) | Yes   | Mouse event. For details, see [MouseEvent](ts-universal-mouse-key.md#mouseevent).|

**Return value**

| Type     | Description                                |
| ------- | ---------------------------------- |
| boolean | Returns **true** if the event is sent successfully; returns **false** otherwise.|

## Example

This example demonstrates how to use the **id** APIs to obtain attributes of a component with the specified by ID and trigger events on that component.

```ts
// xxx.ets
import { IntentionCode } from '@kit.InputKit';

class Utils {
  static rectLeft: number;
  static rectTop: number;
  static rectRight: number;
  static rectBottom: number;
  static rectValue: Record<string, number>;

  // Obtain the coordinates of the rectangular area occupied by the component.
  static getComponentRect(key: string): Record<string, number> {
    let strJson = getInspectorByKey(key);
    let obj: Record<string, string> = JSON.parse(strJson);
    console.info('[getInspectorByKey] current component obj is: ' + JSON.stringify(obj));
    let rectInfo: string[] = JSON.parse('[' + obj.$rect + ']');
    console.info('[getInspectorByKey] rectInfo is: ' + rectInfo);
    Utils.rectLeft = JSON.parse('[' + rectInfo[0] + ']')[0]; // Horizontal coordinate of the upper-left corner of the component relative to the upper-left corner of the window.
    Utils.rectTop = JSON.parse('[' + rectInfo[0] + ']')[1]; // Vertical coordinate of the upper-left corner of the component relative to the upper-left corner of the window.
    Utils.rectRight = JSON.parse('[' + rectInfo[1] + ']')[0]; // Horizontal coordinate of the lower-right corner of the component relative to the upper-left corner of the window.
    Utils.rectBottom = JSON.parse('[' + rectInfo[1] + ']')[1]; // Vertical coordinate of the lower-right corner of the component relative to the upper-left corner of the window.
    return Utils.rectValue = {
      "left": Utils.rectLeft,
      "top": Utils.rectTop,
      "right": Utils.rectRight,
      "bottom": Utils.rectBottom
    };
  };
}

@Entry
@Component
struct IdExample {
  @State text: string = '';

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {

      Button() {
        Text('onKeyTab').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .onKeyEvent(() => {
        this.text = 'onKeyTab';
      })

      Button() {
        Text('click to start').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 })
      .onClick(() => {
        console.info(getInspectorByKey('click'));
        console.info(JSON.stringify(getInspectorTree()));
        this.text = "Button 'click to start' is clicked";
        setTimeout(() => {
          sendEventByKey('longClick', 11, ''); // Send a long press event to the component whose id is "longClick".
        }, 2000)
      }).id('click')

      Button() {
        Text('longClick').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .gesture(
        LongPressGesture().onActionEnd(() => {
          console.info('long clicked');
          this.text = "Button 'longClick' is longclicked";
          setTimeout(() => {
            let rect = Utils.getComponentRect('onTouch'); // Obtain the coordinates of the rectangular area occupied by the component whose ID is "onTouch".
            let touchPoint: TouchObject = {
              id: 1,
              type: TouchType.Down,
              x: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the component.
              y: rect.top + (rect.bottom - rect.top) / 2, // Y coordinate relative to the upper left corner of the component.
              windowX: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the application window.
              windowY: rect.top + (rect.bottom - rect.top) / 2, // Vertical coordinate relative to the upper-left corner of the application window.
              displayX: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the device screen.
              displayY: rect.top + (rect.bottom - rect.top) / 2, // Y-coordinate relative to the upper left corner of the device screen.
              screenX: rect.left + (rect.right - rect.left) / 2, // Horizontal coordinate relative to the upper-left corner of the application window.
              screenY: rect.top + (rect.bottom - rect.top) / 2, // Vertical coordinate relative to the upper-left corner of the application window.
            };
            sendTouchEvent(touchPoint); // Send a touch event.
            touchPoint.type = TouchType.Up;
            sendTouchEvent(touchPoint); // Send a touch event.
          }, 2000)
        })).id('longClick')

      Button() {
        Text('onTouch').fontSize(25).fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule).margin({ top: 20 })
      .onClick(() => {
        console.info('onTouch is clicked');
        this.text = "Button 'onTouch' is clicked";
        setTimeout(() => {
          let rect = Utils.getComponentRect('onMouse'); // Obtain the coordinates of the rectangular area occupied by the component whose ID is "onMouse".
          let mouseEvent: MouseEvent = {
            button: MouseButton.Left,
            action: MouseAction.Press,
            x: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the component.
            y: rect.top + (rect.bottom - rect.top) / 2, // Y coordinate relative to the upper left corner of the component.
            windowX: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the application window.
            windowY: rect.top + (rect.bottom - rect.top) / 2, // Vertical coordinate relative to the upper-left corner of the application window.
            displayX: rect.left + (rect.right - rect.left) / 2, // X coordinate relative to the upper left corner of the device screen.
            displayY: rect.top + (rect.bottom - rect.top) / 2, // Vertical coordinate relative to the upper-left corner of the device screen.
            screenX: rect.left + (rect.right - rect.left) / 2, // Horizontal coordinate relative to the upper-left corner of the application window.
            screenY: rect.top + (rect.bottom - rect.top) / 2, // Vertical coordinate relative to the upper-left corner of the application window.
            stopPropagation: () => {
            },
            timestamp: 1,
            target: {
              area: {
                width: 1,
                height: 1,
                position: {
                  x: 1,
                  y: 1
                },
                globalPosition: {
                  x: 1,
                  y: 1
                }
              }
            },
            source: SourceType.Mouse,
            pressure: 1,
            tiltX: 1,
            tiltY: 1,
            sourceTool: SourceTool.Unknown
          };
          sendMouseEvent(mouseEvent); // Send a mouse event.
        }, 2000)
      }).id('onTouch')

      Button() {
        Text('onMouse').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 }).backgroundColor('#0D9FFB')
      .onMouse(() => {
        console.info('onMouse');
        this.text = "Button 'onMouse' in onMouse";
        setTimeout(() => {
          let keyEvent: KeyEvent = {
            type: KeyType.Down,
            keyCode: 2049,
            keyText: 'tab',
            keySource: 4,
            deviceId: 0,
            metaKey: 0,
            timestamp: 0,
            stopPropagation: () => {
            },
            intentionCode: IntentionCode.INTENTION_DOWN
          };
          sendKeyEvent(keyEvent); // Send a key event.
        }, 2000)
      }).id('onMouse')

      Text(this.text).fontSize(25).padding(15)
    }
    .width('100%').height('100%')
  }
}
```
