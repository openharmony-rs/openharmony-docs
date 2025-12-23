# Interface (WebMessagePort)

通过WebMessagePort可以进行消息的发送以及接收，发送[WebMessageType](./arkts-apis-webview-e.md#webmessagetype10)/[WebMessage](./arkts-apis-webview-t.md#webmessage)类型消息给HTML5侧。

支持使用[@ohos.transfer](../apis-arkts/js-apis-transfer.md)系统对象转换工具进行动静态类型转换。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Interface首批接口从API version 9开始支持。
>
> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 导入模块

```ts
import { webview } from '@kit.ArkWeb';
```

## 属性

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 类型   | 只读 | 可选 | 说明                                              |
| ------------ | ------ | ---- | ---- | ------------------------------------------------|
| isExtentionType<sup>10+</sup> | boolean | 否   | 是 | 创建WebMessagePort时是否指定使用扩展增强接口，[postMessageEventExt](#postmessageeventext10)、[onMessageEventExt](#onmessageeventext10)。<br>true表示使用扩展增强接口，false表示不使用扩展增强接口。<br>默认值：false。   |

## postMessageEvent

postMessageEvent(message: WebMessage): void

发送[WebMessage](./arkts-apis-webview-t.md#webmessage)类型消息给HTML5侧，必须先调用[onMessageEvent](#onmessageevent)，否则会发送失败。完整示例代码参考[postMessage](./arkts-apis-webview-WebviewController.md#postmessage)。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名  | 类型   | 必填 | 说明           |
| ------- | ------ | ---- | :------------- |
| message | [WebMessage](./arkts-apis-webview-t.md#webmessage) | 是   | 要发送的消息。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 17100010 | Failed to post messages through the port. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  ports: webview.WebMessagePort[] = [];

  build() {
    Column() {
      Button('postMessageEvent')
        .onClick(() => {
          try {
            this.ports = this.controller.createWebMessagePorts();
            this.controller.postMessage('__init_port__', [this.ports[0]], '*');
            this.ports[1].postMessageEvent("post message from ets to html5");
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
```ts
// xxx.ets
import { Button, Web, Column, Component, Entry } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  ports: Array<webview.WebMessagePort> = new Array<webview.WebMessagePort>();

  build() {
    Column() {
      Button('postMessageEvent')
        .onClick(() => {
          try {
            this.ports = this.controller.createWebMessagePorts();
            this.controller.postMessage('__init_port__', [this.ports[0]], '*');
            this.ports[1].postMessageEvent("post message from ets to html5");
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## onMessageEvent

onMessageEvent(callback: (result: WebMessage) => void): void

在应用侧的消息端口上注册回调函数，接收HTML5侧发送过来的[WebMessage](./arkts-apis-webview-t.md#webmessage)类型消息。完整示例代码参考[postMessage](./arkts-apis-webview-WebviewController.md#postmessage)。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | :------------------- |
| callback | (result: [WebMessage](./arkts-apis-webview-t.md#webmessage)) => void | 是   | 接收到的消息。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                        |
| -------- | ----------------------------------------------- |
| 17100006 | Failed to register a message event for the port.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed.|

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  ports: webview.WebMessagePort[] = [];

  build() {
    Column() {
      Button('onMessageEvent')
        .onClick(() => {
          try {
            this.ports = this.controller.createWebMessagePorts();
            this.ports[1].onMessageEvent((msg) => {
              if (typeof (msg) == "string") {
                console.info("received string message from html5, string is:" + msg);
              } else if (typeof (msg) == "object") {
                if (msg instanceof ArrayBuffer) {
                  console.info("received arraybuffer from html5, length is:" + msg.byteLength);
                } else {
                  console.info("not support");
                }
              } else {
                console.info("not support");
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
```ts
import {OnPageEndEvent, OnPermissionRequestEvent, OnPageVisibleEvent, Web, Entry, Text, TextInput, TextAttribute, Column, Component, Button, ButtonAttribute } from '@kit.ArkUI'
import { State } from '@ohos.arkui.stateManagement'
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  ports: webview.WebMessagePort[] = [];

  build() {
    Column() {
      Button('onMessageEvent')
        .onClick(() => {
          try {
            this.ports = this.controller.createWebMessagePorts();
            this.ports[1].onMessageEvent((msg) => {
              if (typeof (msg) == "string") {
                console.info("received string message from html5, string is:" + msg);
              } else if (typeof (msg) == "object") {
                if (msg instanceof ArrayBuffer) {
                  console.info("received arraybuffer from html5, length is:" + msg.byteLength);
                } else {
                  console.info("not support");
                }
              } else {
                console.info("not support");
              }
            })
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
          this.controller.postMessage('__init_port__', [this.ports![0]], '*');
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## postMessageEventExt<sup>10+</sup>

postMessageEventExt(message: WebMessageExt): void

发送[WebMessageType](./arkts-apis-webview-e.md#webmessagetype10)类型消息给HTML5侧，必须先调用[onMessageEventExt](#onmessageeventext10)，否则会发送失败。完整示例代码参考[onMessageEventExt](#onmessageeventext10)。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名  | 类型   | 必填 | 说明           |
| ------- | ------ | ---- | :------------- |
| message | [WebMessageExt](./arkts-apis-webview-WebMessageExt.md) | 是   | 要发送的消息。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                              |
| -------- | ------------------------------------- |
| 17100010 | Failed to post messages through the port. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

## onMessageEventExt<sup>10+</sup>

onMessageEventExt(callback: (result: WebMessageExt) => void): void

在应用侧的消息端口上注册回调函数，接收HTML5侧发送过来的[WebMessageType](./arkts-apis-webview-e.md#webmessagetype10)类型消息。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | :------------------- |
| callback | (result: [WebMessageExt](./arkts-apis-webview-WebMessageExt.md)) => void | 是   | 接收到的消息。 |

**错误码：**

以下错误码的详细介绍请参见[Webview错误码](errorcode-webview.md)、[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                        |
| -------- | ----------------------------------------------- |
| 17100006 | Failed to register a message event for the port. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

class TestObj {
  test(str: string): ArrayBuffer {
    let buf = new ArrayBuffer(str.length);
    let buff = new Uint8Array(buf);

    for (let i = 0; i < str.length; i++) {
      buff[i] = str.charCodeAt(i);
    }
    return buf;
  }
}

// 应用与网页互发消息的示例：使用"init_web_messageport"的通道，通过端口0在应用侧接受网页发送的消息，通过端口1在网页侧接受应用发送的消息。
@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  ports: webview.WebMessagePort[] = [];
  nativePort: webview.WebMessagePort | null = null;
  @State msg1: string = "";
  @State msg2: string = "";
  message: webview.WebMessageExt = new webview.WebMessageExt();
  @State testObjtest: TestObj = new TestObj();

  build() {
    Column() {
      Text(this.msg1).fontSize(16)
      Text(this.msg2).fontSize(16)
      Button('SendToH5 setString').margin({
        right: 800,
      })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(1);
              this.message.setString("helloFromEts");
              this.nativePort.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        Button('SendToH5 setNumber').margin({
          top: 10,
          right: 800,
        })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(2);
              this.message.setNumber(12345);
              this.nativePort.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setBoolean').margin({
        top: -90,
      })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(3);
              this.message.setBoolean(true);
              this.nativePort.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setArrayBuffer').margin({
        top: 10,
      })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(4);
              this.message.setArrayBuffer(this.testObjtest.test("Name=test&Password=test"));
              this.nativePort.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setArray').margin({
        top: -90,
        left: 800,
      })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(5);
              this.message.setArray([1, 2, 3]);
              this.nativePort.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setError').margin({
        top: 10,
        left: 800,
      })
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            throw new ReferenceError("ReferenceError");
          }
          catch (error) {
            if (this.nativePort) {
              this.message.setType(6);
              this.message.setError(error);
              this.nativePort.postMessageEventExt(this.message);
            }
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

      Web({ src: $rawfile('index.html'), controller: this.controller })
        .onPageEnd(() => {
          console.info("In ArkTS side message onPageEnd init message channel");
          // 1. 创建消息端口。
          this.ports = this.controller.createWebMessagePorts(true);
          // 2. 发送端口1到HTML5。
          this.controller.postMessage("init_web_messageport", [this.ports[1]], "*");
          // 3. 保存端口0到本地。
          this.nativePort = this.ports[0];
          // 4. 设置回调函数。
          this.nativePort.onMessageEventExt((result) => {
            console.info("In ArkTS side got message");
            try {
              let type = result.getType();
              console.info("In ArkTS side getType:" + type);
              switch (type) {
                case webview.WebMessageType.STRING: {
                  this.msg1 = "result type:" + typeof (result.getString());
                  this.msg2 = "result getString:" + ((result.getString()));
                  break;
                }
                case webview.WebMessageType.NUMBER: {
                  this.msg1 = "result type:" + typeof (result.getNumber());
                  this.msg2 = "result getNumber:" + ((result.getNumber()));
                  break;
                }
                case webview.WebMessageType.BOOLEAN: {
                  this.msg1 = "result type:" + typeof (result.getBoolean());
                  this.msg2 = "result getBoolean:" + ((result.getBoolean()));
                  break;
                }
                case webview.WebMessageType.ARRAY_BUFFER: {
                  this.msg1 = "result type:" + typeof (result.getArrayBuffer());
                  this.msg2 = "result getArrayBuffer byteLength:" + ((result.getArrayBuffer().byteLength));
                  break;
                }
                case webview.WebMessageType.ARRAY: {
                  this.msg1 = "result type:" + typeof (result.getArray());
                  this.msg2 = "result getArray:" + result.getArray();
                  break;
                }
                case webview.WebMessageType.ERROR: {
                  this.msg1 = "result type:" + typeof (result.getError());
                  this.msg2 = "result getError:" + result.getError();
                  break;
                }
                default: {
                  this.msg1 = "default break, type:" + type;
                  break;
                }
              }
            }
            catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          });
        })
    }
  }
}
```

ArkTS-Sta示例：
```ts
import {OnPageEndEvent, OnPermissionRequestEvent, OnPageVisibleEvent, Web, Entry, Text, TextInput, TextAttribute, Column, Component, Button, ButtonAttribute} from '@kit.ArkUI'
import { State } from '@ohos.arkui.stateManagement'
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

class TestObj {
  test(str: string): ArrayBuffer {
    let buf = new ArrayBuffer(str.length);
    let buff = new Uint8Array(buf);

    for (let i = 0; i < str.length; i++) {
      buff[i] = str.charCodeAt(i);
    }
    return buf;
  }
}

// 应用与网页互发消息的示例：使用"init_web_messageport"的通道，通过端口0在应用侧接受网页发送的消息，通过端口1在网页侧接受应用发送的消息。
@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  ports: webview.WebMessagePort[] = [];
  nativePort: webview.WebMessagePort | null = null;
  @State msg1: string = "result type:";
  @State msg2: string = "result getValue：";
  message: webview.WebMessageExt = new webview.WebMessageExt();
  @State testObjtest: TestObj = new TestObj();

  build() {
    Column() {
      Text(this.msg1).fontSize(16)
      Text(this.msg2).fontSize(16)
      Button('SendToH5 setString')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.STRING);
              this.message.setString("helloFromEts");
              this.nativePort?.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setNumber')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.NUMBER);
              this.message.setNumber(12345);
              this.nativePort?.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setBoolean')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.BOOLEAN);
              this.message.setBoolean(true);
              this.nativePort?.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setArrayBuffer')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.ARRAY_BUFFER);
              this.message.setArrayBuffer(this.testObjtest.test("Name=test&Password=test"));
              this.nativePort?.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setArray')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.ARRAY);
              this.message.setArray([1.0, 2.0, 3.0]);
              this.nativePort?.postMessageEventExt(this.message);
            }
          }
          catch (error) {
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('SendToH5 setError')
        .onClick(() => {
          // 使用本侧端口发送消息给HTML5。
          try {
            console.info("In ArkTS side send true start");
            throw new ReferenceError("ReferenceError");
          }
          catch (error : BusinessError) {
            if (this.nativePort) {
              this.message.setType(webview.WebMessageType.ERROR);
              this.message.setError(error);
              this.nativePort?.postMessageEventExt(this.message);
            }
            console.error(`In ArkTS side send message catch error, ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

      Web({src:"resource://rawfile/index.html", controller:this.controller})
        .onPageEnd(() => {
          console.info("In ArkTS side message onPageEnd init message channel");
          // 1. 创建消息端口。
          this.ports = this.controller.createWebMessagePorts(true);
          // 2. 发送端口1到HTML5。
          this.controller.postMessage("init_web_messageport", [this.ports[1]], "*");
          // 3. 保存端口0到本地。
          this.nativePort = this.ports[0];
          // 4. 设置回调函数。
          this.nativePort?.onMessageEventExt((result: webview.WebMessageExt) => {
            console.info("In ArkTS side got message");
            try {
              let type = result.getType();
              console.info("In ArkTS side getType:" + type);
              switch (type) {
                case webview.WebMessageType.STRING: {
                  this.msg1 = "result type:" + typeof (result.getString());
                  this.msg2 = "result getString:" + ((result.getString()));
                  break;
                }
                case webview.WebMessageType.NUMBER: {
                  this.msg1 = "result type:" + typeof (result.getNumber());
                  this.msg2 = "result getNumber:" + ((result.getNumber()));
                  break;
                }
                case webview.WebMessageType.BOOLEAN: {
                  this.msg1 = "result type:" + typeof (result.getBoolean());
                  this.msg2 = "result getBoolean:" + ((result.getBoolean()));
                  break;
                }
                case webview.WebMessageType.ARRAY_BUFFER: {
                  this.msg1 = "result type:" + typeof (result.getArrayBuffer());
                  this.msg2 = "result getArrayBuffer byteLength:" + ((result.getArrayBuffer().byteLength));
                  break;
                }
                case webview.WebMessageType.ARRAY: {
                  this.msg1 = "result type:" + typeof (result.getArray());
                  this.msg2 = "result getArray:" + result.getArray();
                  break;
                }
                case webview.WebMessageType.ERROR: {
                  this.msg1 = "result type:" + typeof (result.getError());
                  this.msg2 = "result getError:" + result.getError();
                  break;
                }
                default: {
                  this.msg1 = "default break, type:" + type;
                  break;
                }
              }
            }
            catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          });
        })
    }
  }
}
```

加载的html文件。
```html
<!--index.html-->
<!DOCTYPE html>
<html lang="en-gb">
<head>
    <title>WebView MessagePort Demo</title>
</head>

<body>
<h1>Html5 Send and Receive Message</h1>
<h3 id="msg">Receive string:</h3>
<h3 id="msg2">Receive arraybuffer:</h3>
<div style="font-size: 10pt; text-align: center;">
    <input type="button" value="Send String" onclick="postStringToApp();" /><br/>
</div>
</body>
<script src="index.js"></script>
</html>
```

<!--code_no_check-->
```js
//index.js
var h5Port;
window.addEventListener('message', function(event) {
    if (event.data == 'init_web_messageport') {
        if(event.ports[0] != null) {
            h5Port = event.ports[0]; // 1. 保存从ets侧发送过来的端口。
            h5Port.onmessage = function(event) {
                console.info("hwd In html got message");
                // 2. 接收ets侧发送过来的消息。
                var result = event.data;
                console.info("In html got message, typeof: ", typeof(result));
                console.info("In html got message, result: ", (result));
                if (typeof(result) == "string") {
                    console.info("In html got message, String: ", result);
                    document.getElementById("msg").innerHTML  =  "String:" + result;
                } else if (typeof(result) == "number") {
                  console.info("In html side got message, number: ", result);
                    document.getElementById("msg").innerHTML = "Number:" + result;
                } else if (typeof(result) == "boolean") {
                    console.info("In html side got message, boolean: ", result);
                    document.getElementById("msg").innerHTML = "Boolean:" + result;
                } else if (typeof(result) == "object") {
                    if (result instanceof ArrayBuffer) {
                        document.getElementById("msg2").innerHTML  =  "ArrayBuffer:" + result.byteLength;
                        console.info("In html got message, byteLength: ", result.byteLength);
                    } else if (result instanceof Error) {
                        console.info("In html error message, err:" + (result));
                        console.info("In html error message, typeof err:" + typeof(result));
                        document.getElementById("msg2").innerHTML  =  "Error:" + result.name + ", msg:" + result.message;
                    } else if (result instanceof Array) {
                        console.info("In html got message, Array");
                        console.info("In html got message, Array length:" + result.length);
                        console.info("In html got message, Array[0]:" + (result[0]));
                        console.info("In html got message, typeof Array[0]:" + typeof(result[0]));
                        document.getElementById("msg2").innerHTML  =  "Array len:" + result.length + ", value:" + result;
                    } else {
                        console.info("In html got message, not any instance of support type");
                        document.getElementById("msg").innerHTML  = "not any instance of support type";
                    }
                } else {
                    console.info("In html got message, not support type");
                    document.getElementById("msg").innerHTML  = "not support type";
                }
            }
            h5Port.onmessageerror = (event) => {
                console.error(`hwd In html Error receiving message: ${event}`);
            };
        }
    }
})

// 使用h5Port往ets侧发送String类型的消息。
function postStringToApp() {
    if (h5Port) {
        console.info("In html send string message");
        h5Port.postMessage("hello");
        console.info("In html send string message end");
    } else {
        console.error("In html h5port is null, please init first");
    }
}
```

## close

close(): void

不需要发送消息时关闭该消息端口。在使用close前，请先使用[createWebMessagePorts](./arkts-apis-webview-WebviewController.md#createwebmessageports)创建消息端口。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

**示例：**

ArkTS-Dyn示例：
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  msgPort: webview.WebMessagePort[] = [];

  build() {
    Column() {
      // 先使用createWebMessagePorts创建端口。
      Button('createWebMessagePorts')
        .onClick(() => {
          try {
            this.msgPort = this.controller.createWebMessagePorts();
            console.info("createWebMessagePorts size:" + this.msgPort.length)
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('close')
        .onClick(() => {
          try {
            if (this.msgPort && this.msgPort.length == 2) {
              this.msgPort[1].close();
            } else {
              console.error("msgPort is null, Please initialize first");
            }
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

ArkTS-Sta示例：
```ts
// xxx.ets
import { Entry, Column, Component, Web, Button } from '@kit.ArkUI';
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController(undefined);
  msgPort: webview.WebMessagePort[] = [] as webview.WebMessagePort[];

  build() {
    Column() {
      // 先使用createWebMessagePorts创建端口。
      Button('createWebMessagePorts')
        .onClick(() => {
          try {
            this.msgPort = this.controller.createWebMessagePorts();
            console.info("createWebMessagePorts size:" + this.msgPort.length)
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Button('close')
        .onClick(() => {
          try {
            if (this.msgPort && this.msgPort.length == 2) {
              this.msgPort[1].close();
              this.msgPort = [];
            } else {
              console.error("msgPort is null, Please initialize first");
            }
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```

## 使用@ohos.transfer进行WebMessagePort类型转换

ArkTS-Dyn中使用ArkTS-Sta的WebMessagePort对象。

- 在ArkTS-Sta模块中将ArkTS-Sta WebMessagePort转换成ArkTS-Dyn WebMessagePort，传入到ArkTS-Dyn子模块`library`中。

  ArkTS-Sta示例：

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, Button } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { WebMessagePortStaticToDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);
    ports: Array<webview.WebMessagePort> = new Array<webview.WebMessagePort>();

    build() {
      Column() {
        Button("WebMessagePort")
          .onClick(() => {
            try {
              this.ports = this.controller.createWebMessagePorts(true);
              let dynamicHandler = transfer.transferDynamic(this.ports[0], 'ArkWeb.WebMessagePort');
              WebMessagePortStaticToDynamic(dynamicHandler);
            } catch (e: Error) {
              console.error('transferDynamic catch error：-----------' + e.message);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
      }
    }
  }
  ```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebMessagePort的方法。

  ArkTS-Dyn示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { webview } from '@kit.ArkWeb';
  export function WebMessagePortStaticToDynamic(handler_: any) {
    try {
      let handler: webview.WebMessagePort = handler_ as webview.WebMessagePort;
      console.info('WebMessagePortStaticToDynamic result=' + handler.isExtentionType);
    } catch (e) {
      console.error('WebMessagePortStaticToDynamic catch Error: ' + e.toString());
    }
  }
  ```

ArkTS-Sta中使用ArkTS-Dyn的WebMessagePort对象。

- 在ArkTS-Dyn模块创建得到ArkTS-Dyn WebMessagePort对象，传给ArkTS-Sta子模块`library`中。

  ArkTS-Dyn示例：

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { WebMessagePortDynamicToStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    ports: webview.WebMessagePort[] = [];

    build() {
      Column() {
        Button("WebMessagePort")
          .onClick(() => {
            try {
              this.ports = this.controller.createWebMessagePorts(true);
              WebMessagePortDynamicToStatic(this.ports[0]);
            } catch (error) {
              console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
            }
          })
        Web({ src: "www.example.com", controller: this.controller })
      }
    }
  }
  ```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录提供接收ArkTS-Dyn WebMessagePort的方法。

  ArkTS-Sta示例：

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';

  export function WebMessagePortDynamicToStatic(dynObject: Object | undefined | null) {
    try {
        let handler: webview.WebMessagePort = transfer.transferStatic(dynObject, 'ArkWeb.WebMessagePort') as webview.WebMessagePort;
        console.info('WebMessagePortDynamicToStatic type=' + handler.isExtentionType);
    } catch (e: Error) {
        console.error('WebMessagePortDynamicToStatic catch error：-----------' + e.message);
    }
  }
  ```