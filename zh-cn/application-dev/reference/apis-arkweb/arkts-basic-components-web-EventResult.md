# Class (EventResult)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhanghaozhi1-->
<!--Designer: @dzichou-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

EventResult是ArkWeb Kit中用于通知Web组件同层事件消费结果的类。在同层嵌入场景下，应用与Web组件共同暴露在事件响应链EventResult允许应用向Web组件声明自身是否消费了触摸或鼠标事件，从而决定Web组件是否继续处理该事件。当应用设置消费结果为true时，表示应用已消费该事件，Web组件将不再消费；当设置为false时，表示应用不消费该事件，事件将由Web组件消费。EventResult触摸事件（[TouchType](../apis-arkui/arkui-ts/ts-appendix-enums.md#touchtype)）和鼠标事件（[MouseAction](../apis-arkui/arkui-ts/ts-appendix-enums.md#mouseaction8)，仅限左中右按键）的消费结果设置，通过[MouseButton](../apis-arkui/arkui-ts/ts-appendix-enums.md#mousebutton8)定义鼠标按键的类型，适用于应用与Web组件同层交互的事件协调场景。

触摸事件示例代码参考[onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11)事件。

鼠标事件示例代码参考[onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent20)事件。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 示例效果请以真机运行为准。

## constructor<sup>12+</sup>

constructor()

EventResult的构造函数。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

## setGestureEventResult<sup>12+</sup>

setGestureEventResult(result: boolean): void

设置手势事件消费结果。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23


**参数：**

| 参数名          | 类型 | 必填  | 说明             |
| --------------- | -------- | ----  |------- |
| result          | boolean  | 是    | 是否消费该手势事件。<br>true表示消费该手势事件，false表示不消费该手势事件。<br>ArkTS-Dyn：传入null或undefined时为true。 <br>ArkTS-Sta：传入undefined时为true。|

**示例：**

请参考[onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11)事件。

## setGestureEventResult<sup>14+</sup>

setGestureEventResult(result: boolean, stopPropagation: boolean): void

设置手势事件消费结果。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名          | 类型 | 必填  | 说明             |
| --------------- | -------- | ----  |------- |
| result          | boolean  | 是    | 是否消费该手势事件。<br>true表示消费该手势事件，false表示不消费该手势事件。<br>ArkTS-Dyn：传入null或undefined时为true。 <br>ArkTS-Sta：传入undefined时为true。|
| stopPropagation | boolean  | 是   | 是否阻止冒泡，在result为true时生效。<br>true表示阻止冒泡，false表示不阻止冒泡。<br>ArkTS-Dyn：传入null或undefined时为true。 <br>ArkTS-Sta：传入undefined时为true。|

**示例：**

请参考[onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11)事件。

## setMouseEventResult<sup>20+</sup>

setMouseEventResult(result: boolean, stopPropagation?: boolean): void

设置鼠标事件消费结果。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名          | 类型 | 必填  | 说明             |
| --------------- | -------- | ----  |------- |
| result          | boolean  | 是    | 是否消费该鼠标事件。<br>true表示消费该鼠标事件，false表示不消费该鼠标事件。<br>传入null或undefined时为true。 |
| stopPropagation | boolean  | 否   | 是否阻止冒泡，在result为true时生效。<br>true表示阻止冒泡，false表示不阻止冒泡。<br>传入null或undefined时为true。<br>默认值：true。 |

**示例：**

请参考[onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent20)事件。

## 使用@ohos.transfer进行EventResult类型转换

ArkTS-Dyn中使用ArkTS-Sta的EventResult对象。

- 在ArkTS-Sta模块中将ArkTS-Sta EventResult转换成ArkTS-Dyn EventResult，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, EventResult, NativeEmbedTouchInfo, $rawfile } from '@ohos.arkui.component';
  import { webview } from '@ohos.web.webview';
  import { transfer } from '@ohos.transfer';
  import { handleEventResultDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .enableNativeEmbedMode(true)
          .onNativeEmbedGestureEvent((event: NativeEmbedTouchInfo): void => {
            console.info('onNativeEmebedGestureEvent invoked');
            try {
                let eventResultDynamic = transfer.transferDynamic(event.result as EventResult, "ArkWeb.EventResult");
                handleEventResultDynamic(eventResultDynamic);
            } catch (e: Error) {
                console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
      }
    }
  }
  ```
  加载的html文件。
  ```html
    <!-- index.html -->
    <!Document>
    <html>
    <head>
        <title>同层渲染测试html</title>
        <meta name="viewport">
    </head>
    <body>
    <div>
        <div id="bodyId">
        <embed id="nativeButton" type = "native/button" width="800" height="800" src="test?params1=1?" style = "background-color:red"/>
        </div>
    </div>
    </body>
    </html>
  ```
- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn EventResult的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleEventResultDynamic(result_: any) {
    let result: EventResult = result_ as EventResult;
    result.setGestureEventResult(false);
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的EventResult对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn EventResult对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleEventResultStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .enableNativeEmbedMode(true)
          .onNativeEmbedGestureEvent((event: NativeEmbedTouchInfo): void => {
            console.info('onNativeEmebedGestureEvent invoked');
            handleEventResultStatic(event.result);
          })
      }
    }
  }
  ```
  加载的html文件。
  ```html
    <!-- index.html -->
    <!Document>
    <html>
    <head>
        <title>同层渲染测试html</title>
        <meta name="viewport">
    </head>
    <body>
    <div>
        <div id="bodyId">
        <embed id="nativeButton" type = "native/button" width="800" height="800" src="test?params1=1?" style = "background-color:red"/>
        </div>
    </div>
    </body>
    </html>
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn EventResult的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { EventResult } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleEventResultStatic(dynObject: Object) {
    try {
        let result: EventResult = transfer.transferStatic(dynObject, "ArkWeb.EventResult") as EventResult;
        result.setGestureEventResult(false);
    } catch (e: Error) {
        console.error('transferStatic catch error：-----------' + e.message);
    }
  }
  ```