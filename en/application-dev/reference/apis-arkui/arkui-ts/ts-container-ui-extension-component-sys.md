# UIExtensionComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @HelloCrease-->

**UIExtensionComponent** is used to embed UIs provided by other applications in the local application UI. The embedded content runs in another process, and the local application does not participate in its layout and rendering.

This component is usually used in modular development scenarios where process isolation is required.

> **NOTE**
>
> This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this component are system APIs.

## Restrictions

This component does not support preview.

The ability to be started must be a UIExtensionAbility, an extension ability with UI. For details about how to implement a UIExtensionAbility, see [@ohos.app.ability.UIExtensionAbility (Base Class for ExtensionAbilities with UI)](../../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

The width and height of the component must be explicitly set to non-zero valid values.

Scrolling to the boundary and then passing the scroll gesture to the upper layer is not supported. When both the UIExtensionComponent and the UIExtensionAbility support content scrolling, using gestures to scroll can cause simultaneous responses inside and outside the **UIExtensionComponent**. This includes but is not limited to scrolling containers such as [Scroll](ts-container-scroll.md), [Swiper](ts-container-swiper.md), [List](ts-container-list.md), and [Grid](ts-container-grid.md). For details about how to avoid the simultaneous scrolling inside and outside the **UIExtensionComponent**, see [Example 2](#example-2-isolating-scrolling-in-uiextensioncomponent-and-external-components).


## Child Components

Not supported

## APIs

UIExtensionComponent(want: Want, options?: UIExtensionOptions)

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                                  | Mandatory| Description          |
| --------------------- | ---------------------------------------------------------- | ---- | ------------------ |
| want                  | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Ability to start. |
| options<sup>11+</sup> | [UIExtensionOptions](#uiextensionoptions11)                | No  | Construction parameters to be transferred.|

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

Universal events, such as the [click event](ts-universal-events-click.md), are not supported.

The events are passed to the remote UIExtensionAbility for processing after coordinate conversion.

The following events are supported:

### onRemoteReady

onRemoteReady(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<UIExtensionProxy>)

Invoked when the connection to the remote UIExtensionAbility is set up, that is, the UIExtensionAbility is ready to receive data through the proxy.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------- |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<UIExtensionProxy>) | Yes| Callback function, which is used to send data to the remote Ability.                         |

### onReceive

onReceive(callback: ReceiveCallback)

Invoked when the data sent by the started UIExtensionAbility is received. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------- |
| callback                        | [ReceiveCallback](#receivecallback18) | Yes| Callback used to return the received data from the remote UIExtensionAbility.                |

### onResult<sup>(deprecated)</sup>

onResult(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<{code: number; want?: Want}>)

Invoked when the started UIExtensionAbility calls **terminateSelfWithResult**. After this callback is invoked, **OnRelease** is invoked.

The result data of the remote UIExtensionAbility can be processed in this callback. For details, see [AbilityResult](../../apis-ability-kit/js-apis-inner-ability-abilityResult.md).

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 12. You are advised to use [onTerminated](#onterminated12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory|Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| code                        | number | Yes| Result code from the remote UIExtensionAbility.                         |
| want                        | Want | No|[Want](../../apis-ability-kit/js-apis-app-ability-want.md) of the result from the remote UIExtensionAbility.|

### onRelease<sup>(deprecated)</sup>

onRelease(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number>)

Invoked when the started UIExtensionAbility is destroyed.

If the UIExtensionAbility is destroyed correctly by calling **terminateSelfWithResult** or **terminateSelf**, the value of **releaseCode** is **0**.

If the UIExtensionAbility is destroyed because it crashes or is forced stopped, the value of **releaseCode** is **1**.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 12. You are advised to use [onTerminated](#onterminated12) or [onError](#onerror) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number> | Yes| Callback function, which is used to obtain the code that indicates how the remote UIExtensionAbility is destroyed. The value **0** means normal destruction, and **1** means abnormal destruction.                         |

### onError

onError(callback:[ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback))

Invoked when an exception occurs during the running of the UIExtensionAbility. You can obtain the error information and handle the error based on the code, name, and message in the callback parameters. For details about service error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback used to return the error information.   |

### onTerminated<sup>12+</sup>

onTerminated(callback: Callback&lt;TerminationInfo&gt;)

Called when the started UIExtensionAbility is terminated by calling **terminateSelfWithResult** or **terminateSelf**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                                                    |
| -------  | ------ | ------ | ------------------------------------------------------------------------------------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](#terminationinfo12)> | Yes| Callback used to return the result from the UIExtensionAbility.|

> **NOTE**
>
> - If the UIExtensionAbility is terminated by calling **terminateSelfWithResult**, the carried information is passed as arguments into the callback function.
> - If the UIExtensionAbility is terminated by calling **terminateSelf**, the input parameters **code** and **want** in the callback function are at their default values: **0** and **undefined**, respectively.

### onDrawReady<sup>18+</sup>

onDrawReady(callback: Callback\<void>)

Called when the UIExtensionAbility draws its first frame.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<void> | Yes| Callback used to return the result. Called when the UIExtensionAbility draws its first frame. The callback is of the void type.   |

### TerminationInfo<sup>12+</sup>

Represents the result returned when the UIExtensionAbility that has been started exits properly by calling **terminateSelfWithResult** or **terminateSelf**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|  Name| Type  | Read-Only|Optional| Description                                                |
| ------- | ------ | ------ | ------ |---------------------------------------------------  |
| code    | number | No| No| Result code returned when the UIExtensionAbility exits. The result code is determined by the data passed when terminateSelfWithResult or terminateSelf is called.|
| want    | [Want](../../apis-ability-kit/js-apis-app-ability-want.md)   | No| Yes| Data returned when the UIExtensionAbility exits.  |

## ReceiveCallback<sup>18+</sup>
type ReceiveCallback = [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\>

Callback function, which is used to encapsulate the data sent by the launched ability.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type  | Description                                                        |
| ------ | --------------------------------------------------------- |
| [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\> | Defines the callback function used to encapsulate the data sent by the launched ability.                |

## UIExtensionOptions<sup>11+</sup>

Describes the optional construction parameters during **UIExtensionComponent** construction.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


| Name              | Type                            | Read-Only| Optional| Description                                                                                                     |
| ----                 | ---------------------------------------- | ---- | ---- | ---------------                                                                                               |
| isTransferringCaller | boolean                                  | No| Yes | Whether the UIExtensionComponent forwards the upper-level caller information when it is used for nesting.<br> Default value: **false**.|
| placeholder<sup>12+</sup> | [ComponentContent](../js-apis-arkui-ComponentContent.md)       | No| Yes  | Placeholder to be displayed before the UIExtensionComponent establishes a connection with the UIExtensionAbility.|
| dpiFollowStrategy<sup>12+</sup> | [DpiFollowStrategy](ts-container-ui-extension-component-sys.md#dpifollowstrategy12)                 | No| Yes  | Whether the DPI settings follow the host or UIExtensionAbility.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**|
| areaChangePlaceholder<sup>14+</sup> | Record<string, [ComponentContent](../js-apis-arkui-ComponentContent.md)>      | No| Yes  | Placeholders for size changes, displayed when the UIExtensionComponent's size changes and the internal rendering of the UIExtension is not completed. The key values support **"FOLD_TO_EXPAND"** (size change for folding and expanding) and **"UNDEFINED"** (default size change).|
| windowModeFollowStrategy<sup>18+</sup> | [WindowModeFollowStrategy](ts-container-ui-extension-component-sys.md#windowmodefollowstrategy18)   | No| Yes  | Following strategy of the window mode.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**|

## DpiFollowStrategy<sup>12+</sup>

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                    | Value | Description            |
| ---------------------------------------- | ----|--------------- |
| FOLLOW_HOST_DPI                  | 0   | The DPI settings follow the host.|
| FOLLOW_UI_EXTENSION_ABILITY_DPI  | 1   | The DPI settings follow the UIExtensionAbility.|

## WindowModeFollowStrategy<sup>18+</sup>

Enumerates the following strategies of the window mode.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                    | Value | Description            |
| ---------------------------------------- | ----|--------------- |
| FOLLOW_HOST_WINDOW_MODE                  | 0   | The window mode follows the host.|
| FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE  | 1   | The window mode follows the UIExtensionAbility.|

## UIExtensionProxy

Implements a **UIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started UIExtensionAbility through the connection established between the two parties.

### send

send(data: Record\<string, Object\>): void

Asynchronously sends data from the component host to the started UIExtensionAbility through the connection established between the two parties.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                    | Mandatory  | Description           |
| ---- | ---------------------------------------- | ---- | --------------- |
| data | Record\<string, Object\> | Yes   | Data to be asynchronously sent to the started UIExtensionAbility. In versions earlier than API version 18, the data type is Object.|

### sendSync<sup>11+</sup>

sendSync(data: Record\<string, Object\>): Record\<string, Object\>

Synchronously sends data from the component host to the started UIExtensionAbility through the connection established between the two parties.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                    | Mandatory  | Description           |
| ---- | ---------------------------------------- | ---- | --------------- |
| data | Record\<string, Object\> | Yes   | Data to be synchronously sent to the started UIExtensionAbility.|

**Return value**

| Type| Description|
| ---- | ----|
| Record\<string, Object\> | Data returned by the UIExtensionAbility.|

**Error codes**

For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).
| ID| Error Message|
| ------- | --------|
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')<sup>11+</sup>

on(type: 'asyncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

Subscribes to asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type|Mandatory| Description|
| ------ | -------- |---- | ------- |
| type   | string | Yes| Event type. The value is fixed at **'asyncReceiverRegister'**.|
| callback   | Callback\<UIExtensionProxy\> | Yes| Callback used to return the result. Callback used to return the result.|

### on('syncReceiverRegister')<sup>11+</sup>

on(type: 'syncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void;

Subscribes to synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type|Mandatory| Description|
| ------ | -------- |---- | ------- |
| type   | string | Yes| Event type. The value is fixed at **'syncReceiverRegister'**.|
| callback   | Callback\<UIExtensionProxy\> | Yes| Callback used to return the result. Callback used to return the result.|

### off('asyncReceiverRegister')<sup>11+</sup>

off(type: 'asyncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description|
| ------ | -------- | ----- | ------- |
| type   | string | Yes| Event type. The value is fixed at **'asyncReceiverRegister'**.|
| callback | Callback\<UIExtensionProxy\> | No| Callback used to return the result. If this parameter is left blank, the callback is triggered after asynchronous registration of all extended abilities is canceled.<br> If this parameter is not set, this API unsubscribes from all callbacks corresponding to **type**.|

### off('syncReceiverRegister')<sup>11+</sup>

off(type: 'syncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description|
| ------ | -------- | ----- | ------- |
| type   | string | Yes| Event type. The value is fixed at **'syncReceiverRegister'**.|
| callback | Callback\<UIExtensionProxy\> | No| Callback used to return the result. If this parameter is left blank, the callback is triggered after all extended abilities are unsubscribed from and synchronously registered.<br> If this parameter is not set, this API unsubscribes from all callbacks corresponding to **type**.|

## Example

### Example 1: Loading a UIExtension

The use of the **UIExtensionComponent** is divided into the user side and the provider side. This example shows only the method used by the component and the UIExtensionAbility. For the code to run properly, you need to install the ability whose **bundleName** is **"com.example.newdemo"** and **abilityName** is **"UIExtensionProvider"** on the device.

**User Side**

The entry point file **Index.ets** for the user side is as follows:
```ts
import { ComponentContent } from '@kit.ArkUI';

class Params {
}
@Builder
function LoadingBuilder(params: Params) {
  Column() {
   LoadingProgress()
      .color(Color.Blue)
  }
}
@Builder
function AreaChangePlaceholderBuilder(params: Params) {
  Column() {
  }
  .width('100%')
  .height('100%')
  .backgroundColor(Color.Orange)
}
@Entry
@Component
struct Second {
  @State message1: string = 'Hello World 1';
  @State message2: string = 'Hello World 2';
  @State message3: string = 'Hello World 3';
  @State visible: Visibility = Visibility.Hidden;
  @State wid: number = 300;
  @State hei: number = 300;
  @State windowStrategy: WindowModeFollowStrategy = WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE;
  private proxy: UIExtensionProxy | null = null;
  private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params);
  private areaChangePlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(AreaChangePlaceholderBuilder), new Params);


  build() {
    Row() {
      Column() {
        Text(this.message1).fontSize(30)
        Text(this.message2).fontSize(30)
        Text(this.message3).fontSize(30)
        UIExtensionComponent({
          bundleName : "com.example.newdemo",
          abilityName: "UIExtensionProvider",
          parameters: {
            "ability.want.params.uiExtensionType": "sys/commonUI"
          }},
          {
            placeholder: this.initPlaceholder,
            areaChangePlaceholder: {
              "FOLD_TO_EXPAND" : this.areaChangePlaceholder,
            },
            windowModeFollowStrategy: this.windowStrategy
          })
          .width(this.wid)
          .height(this.hei)
          .border({width: 5, color: Color.Blue})
          .onReceive((data) => {
            console.info('Lee onReceive, for test');
            this.message3 = JSON.stringify(data['data']);
          })
          .onError((info) => {
            console.error(`onError: code = ${info.code}`);
          })
          .onTerminated((info) => {
            console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
          })
          .onRemoteReady((proxy) => {
            console.info('onRemoteReady, for test');
            this.proxy = proxy;

            this.proxy.on("syncReceiverRegister", syncRegisterCallback1);

            this.proxy.on("asyncReceiverRegister", (proxy1) => {
              console.info("on invoke for test, type is asyncReceiverRegister");
            });
          })

        Button("Send to UIExtensionAbility").onClick(() => {
          if (this.proxy != undefined) {
            this.proxy.send({data: "Hello 1"});

            try {
              let re = this.proxy.sendSync({data: "Hello 2"});
              console.info("for test, re=" + JSON.stringify(re));
            } catch (err) {
              console.error(`sendSync failed for test. errCode=${err.code}, msg=${err.message}`);
            }
          }
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}

function syncRegisterCallback1(proxy: UIExtensionProxy) {
  console.info("on invoke for test, syncRegisterCallback1, type is syncReceiverRegister");
}

function syncRegisterCallback2(proxy: UIExtensionProxy) {
  console.info("on invoke for test, syncRegisterCallback2, type is syncReceiverRegister");
}
```
**Provider Side**

Perform the following:
- Add the extension entry point file: **/src/main/ets/uiextensionability/UIExtensionProvider.ets**.
```ts
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[UIExtAbility]'
export default class UIExtAbility extends UIExtensionAbility {

  onCreate() {
    console.info(TAG, `UIExtAbility onCreate`);
  }

  onForeground() {
    console.info(TAG, `UIExtAbility onForeground`);
  }

  onBackground() {
    console.info(TAG, `UIExtAbility onBackground`);
  }

  onDestroy() {
    console.info(TAG, `UIExtAbility onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `UIExtAbility onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    session.loadContent('pages/extension', storage);
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `UIExtAbility onSessionDestroy`);
  }
}
```

- Modify the extension ability entry page file: **/src/main/ets/pages/extension.ets**
```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';

let storage = new LocalStorage();
AppStorage.setOrCreate('message', 'UIExtensionAbility');

@Entry(storage)
@Component
struct Extension {
  @StorageLink('message') storageLink: string = '';
  private session: UIExtensionContentSession | undefined = storage.get<UIExtensionContentSession>('session');
  pathStack: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === "hello") {
      pageOneTmp();
    }
  }

  onPageShow() {
    if (this.session != undefined) {
      this.session.setReceiveDataCallback((data)=> {
        this.storageLink = JSON.stringify(data);
        console.info("invoke for test, handle callback set by setReceiveDataCallback successfully");
      })

      this.session.setReceiveDataForResultCallback(func1);
    }
  }

  build() {
    Navigation(this.pathStack) {
      Row() {
        Column() {
          Text(this.storageLink)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          Button("Send to Component").onClick(()=>{
            if (this.session != undefined) {
              this.session.sendData({"data": 543321});
              console.info('send 543321, for test');
            }
          })
          Button("terminate").onClick(()=> {
            if (this.session != undefined) {
              this.session.terminateSelf();
            }
            storage.clear();
          })
          Button("terminate with result").onClick(()=>{
            if (this.session != undefined) {
              this.session.terminateSelfWithResult({
                resultCode: 0,
                want: {
                  bundleName: "myBundleName",
                  parameters: { "result": 123456 }
                }
              });
            }
            storage.clear();
          })

          Button("Redirect").onClick(()=> {
            this.pathStack.pushPath({ name: "hello"});
          })
        }
      }
      .height('100%')
    }.navDestination(this.PageMap)
    .mode(NavigationMode.Stack)
  }
}

// pageOne
@Component
export struct pageOneTmp {
  pathStack: NavPathStack = new NavPathStack()

  build() {
    NavDestination() {
      Column() {
        Text("Hello World")
      }.width('100%').height('100%')
    }.title("pageOne")
    .onBackPressed(() => {
      const popDestinationInfo = this.pathStack.pop(); // Pop the top element out of the navigation stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}

function func1(data: Record<string, Object>): Record<string, Object> {
  let linkToMsg: SubscribedAbstractProperty<string> = AppStorage.link('message');
  linkToMsg.set(JSON.stringify(data));
  console.info("invoke for test, handle callback set by setReceiveDataForResultCallback successfully");
  return data;
}

```

- Modify the extension ability module configuration file: **/src/main/module.json5**.
```json
{
    "name": "UIExtensionProvider",
    "srcEntry": "./ets/uiextensionability/UIExtensionProvider.ets",
    "description": "1",
    "label": "$string:EntryAbility_label",
    "type": "sys/commonUI",
    "exported": true,
}
```

### Example 2: Isolating Scrolling in UIExtensionComponent and External Components

This example demonstrates how to handle simultaneous scrolling in both the UIExtensionComponent and the external container. When both the UIExtensionComponent and the external container use the [Scroll](ts-container-scroll.md) container, you can isolate the scrolling behavior by intercepting gestures on the UIExtensionComponent. This ensures that when the user scrolls inside the UIExtensionComponent, the external container does not respond to the scroll gesture.

Gesture handling:
Internal scrolling: scrolling within the component using touch gestures
External scrolling: scrolling of the outer container using the scrollbar

For the code to run properly, you need to install the ability whose **bundleName** is **"com.example.newdemo"** and **abilityName** is **"UIExtensionProvider"** on the device.

The provider side remains the same as in [Example 1](#example-1-loading-a-uiextension).

The entry point file **UIExtensionProvider.ets** and the module configuration file** module.json5** are identical to those in [Example 1](#example-1-loading-a-uiextension).

- Provider side implementation:
```ts
@Entry
@Component
struct Second {
  @State message1: string = 'Hello World 1';
  @State message2: string = 'Hello World 2';
  @State message3: string = 'Hello World 3';
  @State visible: Visibility = Visibility.Hidden;
  @State wid: number = 300;
  @State hei: number = 300;
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      // Scrollable container component.
      Scroll(this.scroller) {
        Column() {
          Text(this.message1).fontSize(30)
          Text(this.message2).fontSize(30)
          Text(this.message3).fontSize(30)

          // Repeat components to create scrollable content.
          ForEach(this.arr, (item: number) => {
            UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
              })
              .width(this.wid)
              .height(this.hei)
               // Use gesture interception to prevent external components from responding to scrolling.
              .gesture(PanGesture().onActionStart(() => {
                console.info('UIExtensionComponent PanGesture onAction');
              }))
              .border({ width: 5, color: Color.Blue })
              .onReceive((data) => {
                console.info('Lee onReceive, for test');
                this.message3 = JSON.stringify(data['data']);
              })
              .onTerminated((info) => {
                console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
              })
              .onRemoteReady((proxy) => {
                console.info('onRemoteReady, for test');
              })
            }, (item: string) => item)
        }
        .width('100%')
      }
      .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
      .scrollBar(BarState.On) // The scrollbar is always displayed.
      .scrollBarColor(Color.Gray) // The scrollbar color is gray.
      .scrollBarWidth(10) // The scrollbar width is 10.
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })
    }
    .height('100%')
  }
}
```

- Entry file **extension.ets** for the provider side:
```ts
@Entry
@Component
struct Extension {
  @StorageLink('message') storageLink: string = '';
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8];

  build() {
    Column() {
      // Scrollable container component.
      Scroll(this.scroller) {
        Column() {
          Text('Test demo')
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          // Repeat components to create scrollable content.
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(Color.Pink)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: string) => item)
        }
      }

    }
    .height('100%')
  }
}
```
