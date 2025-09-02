# 组件标识
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @HelloCrease-->

id为组件的唯一标识，在整个应用内唯一。本模块提供组件标识相关接口，可以获取指定id组件的属性，也提供向指定id组件发送事件的功能。

>  **说明：**
>
> - 从API Version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 若同一个组件设置了多个id或者key，最后设置的生效。


## id

id(value: string): T

组件的唯一标识，唯一性由使用者保证。当未设置id时，组件默认id为空。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型      | 必填 | 说明                       |
| ------ | -------- | -----|---------------------- |
| value  | string   |  是  | 组件的唯一标识，唯一性由使用者保证。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## key<sup>12+</sup>

key(value: string): T

组件的唯一标识，唯一性由使用者保证。

此接口仅用于对应用的测试。与id同时使用时，后赋值的属性会覆盖先赋值的属性，建议仅设置id。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型      | 必填 | 说明                       |
| ------ | -------- | -----|---------------------- |
| value   | string   | 是 | 组件的唯一标识，唯一性由使用者保证。<br>默认值：''<br/> |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## 基于组件标识的拓展能力

组件标识的拓展能力仅用于对应用的测试，以下各个接口示例，需要在应用工程的ohosTest/ets/test目录中调试，具体可以参考[自动化测试框架使用指导 ](../../../../application-dev/application-test/arkxtest-guidelines.md)。

### getInspectorByKey<sup>9+</sup>

getInspectorByKey(id: string): string

获取指定id的组件的所有属性，不包括子组件信息。

此接口仅用于对应用的测试，使用时建议等应用启动且布局完成后再调用此接口。由于耗时长，不建议测试之外的场景使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数:**

| 参数名   | 类型      | 必填     | 说明        |
| ---- | -------- | ---- | -------------|
| id   | string   | 是    | 要获取属性的组件id。 |

**返回值:**

| 类型        | 说明             |
| -------| -------------- |
| string | 组件属性列表的JSON字符串。<br />**说明**：<br /> 字符串信息包含组件的tag、id、位置信息(相对于窗口左上角的坐标)以及用于测试检查的组件所包含的相关属性信息。组件中每个字段的含义请参考[getInspectorInfo](../js-apis-arkui-frameNode.md#getinspectorinfo12)的返回值说明。 |

**示例:**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
        .onClick(() => {
          console.info(`Text is clicked`);
        })
      Button('TEST BUTTON').onClick(() => {
        let result = getInspectorByKey("TEXT");
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

获取组件树及组件属性。

此接口仅用于对应用的测试。由于耗时长，不建议使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**返回值:**

| 类型     | 说明                            |
| ------ | --------------------------- |
| Object | 组件树及组件属性列表的JSON对象。组件中每个字段的含义请参考[getInspectorInfo](../js-apis-arkui-frameNode.md#getinspectorinfo12)的返回值说明。 |

**示例:**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
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

给指定id的组件发送事件。

此接口仅用于对应用的测试。由于耗时长，不建议使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数:**

| 参数名       | 类型      | 必填       | 说明                         |
| ------ | -------| ---- | -------------------------- |
| id     | string | 是    | 要触发事件的组件的id。                      |
| action | number | 是    | 要触发的事件类型，目前支持取值：<br/>-&nbsp;点击事件Click:&nbsp;10。<br/>-&nbsp;长按事件LongClick:&nbsp;11。 |
| params | string | 是    | 事件参数，无参数传空字符串&nbsp;""。            |

**返回值:**

| 类型          | 说明                         |
| -------- | --------------------------|
| boolean  | 找不到指定id的组件时返回false，其余情况返回true。 |

**示例:**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
        .onClick(() => {
          console.info(`Text is clicked`);
        })
      Button('TEST BUTTON').onClick(() => {
        sendEventByKey("TEXT", 10, "");
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### sendTouchEvent<sup>9+</sup>

sendTouchEvent(event: TouchObject): boolean

发送触摸事件。

此接口仅用于对应用的测试。由于耗时长，不建议使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数:**

| 参数名      | 类型            | 必填  | 说明                                                         |
| ----- | ----------- | ---- | ------------------------------------------------------------ |
| event | [TouchObject](ts-universal-events-touch.md#touchobject对象说明) | 是    | 触发触摸事件的位置，event参数见[TouchObject](ts-universal-events-touch.md#touchobject对象说明)的介绍。 |

**返回值:**

| 类型      | 说明                         |
| ------- | ---------------------------|
| boolean | 事件发送失败时返回false，其余情况返回true。 |

### sendKeyEvent<sup>9+</sup>

sendKeyEvent(event: KeyEvent): boolean

发送按键事件。

此接口仅用于对应用的测试。由于耗时长，不建议使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数:**

| 参数名    | 类型     | 必填      | 说明                                                         |
| ----- | -------- | ----  | ------------------------------------------------------------ |
| event | [KeyEvent](ts-universal-events-key.md#keyevent对象说明) | 是     | 按键事件，event参数见[KeyEvent](ts-universal-events-key.md#keyevent对象说明)介绍。 |

**返回值:**

| 类型      | 说明                           |
| ------- | ------------------------------|
| boolean | 事件发送失败时时返回false，其余情况返回true。 |

### sendMouseEvent<sup>9+</sup>

sendMouseEvent(event: MouseEvent): boolean

发送鼠标事件。

此接口仅用于对应用的测试。由于耗时长，不建议使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名     | 类型       | 必填       | 说明                                     |
| ----- | ---------- | ----  | --------------------------------------- |
| event | [MouseEvent](ts-universal-mouse-key.md#mouseevent对象说明) | 是    | 鼠标事件，event参数见[MouseEvent](ts-universal-mouse-key.md#mouseevent对象说明)介绍。 |

**返回值：**

| 类型      | 说明                                 |
| ------- | ---------------------------------- |
| boolean | 事件发送失败时返回false，其余情况返回true。 |

## 示例

该示例主要展示如何通过组件标识接口，获取特定id组件的属性，以及如何向该id的组件触发事件。

```ts
// xxx.ets
import { IntentionCode } from '@kit.InputKit';

class Utils {
  static rect_left: number;
  static rect_top: number;
  static rect_right: number;
  static rect_bottom: number;
  static rect_value: Record<string, number>;

  //获取组件所占矩形区域坐标
  static getComponentRect(key:string):Record<string, number> {
    let strJson = getInspectorByKey(key);
    let obj:Record<string, string> = JSON.parse(strJson);
    console.info("[getInspectorByKey] current component obj is: " + JSON.stringify(obj));
    let rectInfo:string[] = JSON.parse('[' + obj.$rect + ']');
    console.info("[getInspectorByKey] rectInfo is: " + rectInfo);
    Utils.rect_left = JSON.parse('[' + rectInfo[0] + ']')[0];     // 相对于组件左上角的水平方向坐标
    Utils.rect_top = JSON.parse('[' + rectInfo[0] + ']')[1];     // 相对于组件左上角的垂直方向坐标
    Utils.rect_right = JSON.parse('[' + rectInfo[1] + ']')[0];    // 相对于组件右下角的水平方向坐标
    Utils.rect_bottom = JSON.parse('[' + rectInfo[1] + ']')[1];   // 相对于组件右下角的垂直方向坐标
    return Utils.rect_value = {
      "left": Utils.rect_left, "top": Utils.rect_top, "right": Utils.rect_right, "bottom": Utils.rect_bottom
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
        this.text = "onKeyTab";
      })

      Button() {
        Text('click to start').fontSize(25).fontWeight(FontWeight.Bold)
      }.margin({ top: 20 })
      .onClick(() => {
        console.info(getInspectorByKey("click"));
        console.info(JSON.stringify(getInspectorTree()));
        this.text = "Button 'click to start' is clicked";
        setTimeout(() => {
          sendEventByKey("longClick", 11, ""); // 向id为"longClick"的组件发送长按事件
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
          let rect = Utils.getComponentRect('onTouch'); // 获取id为"onTouch"组件的矩形区域坐标
          let touchPoint: TouchObject = {
            id: 1,
            type: TouchType.Down,
            x: rect.left + (rect.right - rect.left) / 2, // 相对于组件左上角的水平方向坐标
            y: rect.top + (rect.bottom - rect.top) / 2, // 相对于组件左上角的垂直方向坐标
            screenX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标，API10已废弃，采用windowX替代
            screenY: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的垂直方向坐标，API10已废弃，采用windowY替代
            windowX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
            windowY: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的垂直方向坐标
            displayX: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的水平方向坐标
            displayY: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的垂直方向坐标
          };
          sendTouchEvent(touchPoint); // 发送触摸事件
          touchPoint.type = TouchType.Up;
          sendTouchEvent(touchPoint); // 发送触摸事件
        }, 2000)
      })).id('longClick')

      Button() {
        Text('onTouch').fontSize(25).fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule).margin({ top: 20 })
      .onClick(() => {
        console.info('onTouch is clicked');
        this.text = "Button 'onTouch' is clicked";
        setTimeout(() => {
          let rect = Utils.getComponentRect('onMouse'); // 获取id为"onMouse"组件的矩形区域坐标
          let mouseEvent: MouseEvent = {
            button: MouseButton.Left,
            action: MouseAction.Press,
            x: rect.left + (rect.right - rect.left) / 2, // 相对于组件左上角的水平方向坐标
            y: rect.top + (rect.bottom - rect.top) / 2, // 相对于组件左上角的垂直方向坐标
            screenX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标，API10已废弃，采用windowX替代
            screenY: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的垂直方向坐标，API10已废弃，采用windowY替代
            windowX: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的水平方向坐标
            windowY: rect.left + (rect.right - rect.left) / 2, // 相对于应用窗口左上角的垂直方向坐标
            displayX: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的水平方向坐标
            displayY: rect.left + (rect.right - rect.left) / 2, // 相对于设备屏幕左上角的垂直方向坐标
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
          sendMouseEvent(mouseEvent); // 发送鼠标事件
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
          sendKeyEvent(keyEvent); // 发送按键事件
        }, 2000)
      }).id('onMouse')

      Text(this.text).fontSize(25).padding(15)
    }
    .width('100%').height('100%')
  }
}
```
