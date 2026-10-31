# UIExtensionComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7a9882ee5242543d92919229e2e1f78806e99a9b translatedAt=2026-08-21T02:28:17.848Z pushedAt=2026-08-22T03:24:31.781Z -->

**UIExtensionComponent** is used to embed UIs provided by other apps in the local page. The displayed content runs in another process, and the local app does not participate in its layout or rendering. Through process isolation, secure UI isolation and crash isolation between apps can be achieved, while supporting independent development and deployment of modules.

It is usually used in modular development scenarios where process isolation is required, such as embedding functional modules provided by third-party apps and implementing UI capability extension between apps.

> **NOTE**
>
> - This component is supported since API version 10. New APIs added in later versions will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs provided by this module are system APIs.

## Constraints

This component does not support preview.

The launched Ability (app component) must be a UI-enabled Ability extension. For details about how to implement a UI-enabled Ability extension, see [UIExtensionAbility Component](../../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

The width and height of the component must be explicitly set to non-zero valid values.

The scenario where scrolling continues after the edge is reached is not supported. When both the **UIExtensionComponent** host and the UIExtensionAbility support content scrolling, gesture-based scrolling will cause simultaneous responses from both inside and outside the **UIExtensionComponent**. This includes, but is not limited to, scrollable containers such as [Scroll](ts-container-scroll.md), [Swiper](ts-container-swiper.md), [List](ts-container-list.md), and [Grid](ts-container-grid.md). For details about how to avoid the simultaneous scrolling inside and outside the **UIExtensionComponent**, see [Example 2](#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent).

## Child Components

Not supported

## APIs

UIExtensionComponent(want: Want, options?: UIExtensionOptions)

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                                  | Mandatory| Description          |
| --------------------- | ---------------------------------------------------------- | ---- | ------------------ |
| want                  | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Ability to load, which must be a UI-capable Ability extension. In the **parameters** of Want, set the **ability.want.params.uiExtensionType** field, whose value must be consistent with the type configured for the extension Ability in **module.json5**.  |
| options<sup>11+</sup> | [UIExtensionOptions](#uiextensionoptions11) | No | Construction parameters to pass, used to customize the configuration of **UIExtensionComponent** (such as setting the placeholder, DPI following policy, window mode following policy, etc.). Pass this parameter when the preceding configurations need to be customized; otherwise, the default configuration is used. |

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

Universal events, such as the [click event](ts-universal-events-click.md), are not supported.

The component converts the coordinates of the event and then passes it to the launched Ability for processing.

The following events are supported:

### onRemoteReady

onRemoteReady(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<UIExtensionProxy>)

Invoked when the connection to the remote UIExtensionAbility is set up, that is, the UIExtensionAbility is ready to receive data through the proxy.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------- |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](#uiextensionproxy)> | Yes | Callback invoked when the **UIExtensionAbility** is connected. The input parameter is **UIExtensionProxy**, through which data can be sent to the launched **Ability**.                          |

### onReceive

onReceive(callback: ReceiveCallback)

Invoked when the data sent by the started UIExtensionAbility is received. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------- |
| callback | [ReceiveCallback](#receivecallback18) | Yes | Callback invoked to return the data received from the launched Ability. |

### onResult<sup>(deprecated)</sup>

onResult(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<{code: number; want?: Want}>)

When the launched Ability extension calls **terminateSelfWithResult**, this callback is invoked first, and then **onRelease** is invoked.

The result data of the launched **Ability** can be processed in this callback. For details, see [AbilityResult](../../apis-ability-kit/js-apis-inner-ability-abilityResult.md).

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 12. You are advised to use [onTerminated](#onterminated12) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory|Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<{code: number; want?: [Want](../../apis-ability-kit/js-apis-app-ability-want.md)}> | Yes | Callback invoked to return the result data when the launched **Ability** extension calls **terminateSelfWithResult**.                          |

### onRelease<sup>(deprecated)</sup>

onRelease(callback: [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number>)

Invoked when the started UIExtensionAbility is destroyed.

If the UIExtensionAbility is destroyed correctly by calling **terminateSelfWithResult** or **terminateSelf**, the value of **releaseCode** is **0**.

If the UIExtensionAbility is destroyed because it crashes or is forced stopped, the value of **releaseCode** is **1**.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 12. You are advised to use [onTerminated](#onterminated12) and [onError](#onerror) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<number> | Yes| Callback invoked to return the code when the ability is destroyed. The value **0** indicates that the ability is destroyed normally, and the value **1** indicates that the ability is destroyed abnormally.                         |

### onError

onError(callback:[ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback))

Invoked when an error occurs during the running of the UIExtensionAbility. Through the **code**, **name**, and **message** in the callback parameters, error information can be obtained and handled. For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback. It returns the error information.   |

### onTerminated<sup>12+</sup>

onTerminated(callback: Callback&lt;TerminationInfo&gt;)

Called when the started UIExtensionAbility is terminated by calling **terminateSelfWithResult** or **terminateSelf**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                                                    |
| -------  | ------ | ------ | ------------------------------------------------------------------------------------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](#terminationinfo12)> | Yes| Callback used to return the result from the **UIExtensionAbility**. The type is [TerminationInfo](#terminationinfo12). |

> **NOTE**
>
> - If the UIExtensionAbility is terminated by calling **terminateSelfWithResult**, the carried information is passed as arguments into the callback function.
> - If the UIExtensionAbility is terminated by calling **terminateSelf**, the input parameters **code** and **want** in the callback will take their default values: **0** and **undefined**, respectively.

### onDrawReady<sup>18+</sup>

onDrawReady(callback: Callback\<void>)

Triggered when the started UIExtensionAbility draws the first frame.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                      | Type  | Mandatory| Description                                                        |
| ---------------------------- | ------ | ------ | ------------------------------------------------------------ |
| callback                        | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<void> | Yes| Callback. It is called when the UIExtensionAbility draws its first frame. The type is void.   |

### TerminationInfo<sup>12+</sup>

Triggered when the started UIExtensionAbility exits properly by calling **terminateSelfWithResult** or **terminateSelf**.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|  Name| Type  | Read-Only|Optional| Description                                                |
| ------- | ------ | ------ | ------ |---------------------------------------------------  |
| code    | number | No | No | Result code returned when the launched **UIExtensionAbility** exits. The result code is determined by the data passed in when `terminateSelfWithResult` or `terminateSelf` is called. |
| want    | [Want](../../apis-ability-kit/js-apis-app-ability-want.md)   | No | Yes | Data returned when the launched **UIExtensionAbility** exits. The default value is **undefined**.   |

## ReceiveCallback<sup>18+</sup>

type ReceiveCallback = [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\>

Triggered to encapsulate the data sent by the started ability.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type  | Description                                                        |
| ------ | --------------------------------------------------------- |
| [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\> | Callback invoked to encapsulate the data sent by the started ability.                |

## UIExtensionOptions<sup>11+</sup>

Used to pass optional construction parameters when the **UIExtensionComponent** is constructed.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name              | Type                            | Read-Only| Optional| Description                                                                                                     |
| ----                 | ---------------------------------------- | ---- | ---- | ---------------                                                                                               |
| isTransferringCaller | boolean                                  | No | Yes  | Whether to forward the Caller information of the previous level when **UIExtensionComponent** is nested. The value **true** indicates that the Caller information of the previous level is forwarded, and **false** indicates that it is not forwarded.<br> Default value: **false** |
| placeholder<sup>12+</sup> | [ComponentContent](../js-apis-arkui-ComponentContent.md) | No | Yes | Placeholder displayed before the connection between **UIExtensionComponent** and **UIExtensionAbility** is established. Pass this parameter when a loading state or prompt content needs to be displayed to users before the connection is established. If this parameter is not set, no placeholder content is displayed by default. |
| dpiFollowStrategy<sup>12+</sup> | [DpiFollowStrategy](#dpifollowstrategy12)                 | No | Yes   | Provides an API for setting whether the DPI follows the host or the **UIExtensionAbility**.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI** |
| areaChangePlaceholder<sup>14+</sup> | Record<string, [ComponentContent](../js-apis-arkui-ComponentContent.md)>      | No | Yes   | Placeholder displayed when the size of **UIExtensionComponent** changes and the internal rendering of **UIExtensionAbility** is not complete. The key supports only "FOLD_TO_EXPAND" (fold-to-expand size change) and "UNDEFINED" (default size change). Other key values do not take effect. If this parameter is not set, no size-change placeholder content is displayed by default. |
| windowModeFollowStrategy<sup>18+</sup> | [WindowModeFollowStrategy](#windowmodefollowstrategy18)   | No | Yes   | Provides an API for setting the window mode so that it follows the host or the **UIExtensionAbility**.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE** |

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

Used for the component user to send data to the launched Ability and to subscribe to and unsubscribe from the registration events of the extension Ability after a connection is successfully established between the two parties.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### send

send(data: Record\<string, Object\>): void

Used in the scenario where the component user sends data to the launched Ability after a connection is successfully established between the two parties, providing asynchronous data sending.

> **NOTE**
> Both **send** and **sendSync** can be used to send data to the launched Ability. **send** is asynchronous and has no return value, and is suitable for scenarios where the reply from the extension Ability is not required. **sendSync** is synchronous and can obtain the reply data from the extension Ability, and is suitable for scenarios where the processing result needs to be obtained synchronously.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                    | Mandatory  | Description           |
| ---- | ---------------------------------------- | ---- | --------------- |
| data | Record\<string, Object\> | Yes | Data asynchronously sent to the launched **UIExtensionAbility**. In versions earlier than API version 18, the type of data is Object. |

### sendSync<sup>11+</sup>

sendSync(data: Record\<string, Object\>): Record\<string, Object\>

Used in the scenario where the component user sends data to the launched Ability after a connection is successfully established between the two parties, providing synchronous data sending.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                    | Mandatory  | Description           |
| ---- | ---------------------------------------- | ---- | --------------- |
| data | Record\<string, Object\> | Yes | Data synchronously sent to the launched **UIExtensionAbility**. Before API version 18, the type of data is Object. |

**Return value**

| Type | Description |
| ---- | ----|
| Record\<string, Object\> | Data replied by the extension Ability. |

**Error codes**

For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

| ID| Error Message|
| ------- | --------|
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')<sup>11+</sup>

on(type: 'asyncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

Subscribes to asynchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

> **NOTE**
> **asyncReceiverRegister** and **syncReceiverRegister** subscribe to the asynchronous and synchronous data receiving registration events of the extension Ability, respectively. When the extension Ability calls **setReceiveDataCallback** to register asynchronous receiving, the **asyncReceiverRegister** callback is triggered. When the extension Ability calls **setReceiveDataForResultCallback** to register synchronous receiving, the **syncReceiverRegister** callback is triggered. Developers should select the corresponding event to subscribe to based on the data receiving mode used by the extension Ability.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type|Mandatory| Description|
| ------ | -------- |---- | ------- |
| type   | string | Yes | Event type. The value is **'asyncReceiverRegister'**, indicating subscription to the asynchronous registration callback of the extended Ability. |
| callback   | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](#uiextensionproxy)> | Yes | Callback invoked when the extended Ability registers **setReceiveDataCallback**. |

### on('syncReceiverRegister')<sup>11+</sup>

on(type: 'syncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

Subscribes to synchronous registration of the started UIExtensionAbility through the connection established between the component host and UIExtensionAbility.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type|Mandatory| Description|
| ------ | -------- |---- | ------- |
| type   | string | Yes | Event type. The value is **'syncReceiverRegister'**, indicating subscription to the synchronous registration callback of the extension Ability. |
| callback   | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](#uiextensionproxy)> | Yes | Callback invoked when the extension Ability registers **setReceiveDataForResultCallback**. |

### off('asyncReceiverRegister')<sup>11+</sup>

off(type: 'asyncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Used in the scenario where the component user unsubscribes from the asynchronous registration event of the launched Ability after a connection is successfully established between the two parties. This method is used together with **on('asyncReceiverRegister')** to cancel the subscription registered through **on('asyncReceiverRegister')**. When it is no longer necessary to listen for the asynchronous registration event (for example, before the component is destroyed), call this method to unsubscribe to avoid the callback being unable to be released.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description|
| ------ | -------- | ----- | ------- |
| type   | string | Yes | Event type. The value is **'asyncReceiverRegister'**, which indicates unsubscribing from the asynchronous registration callback of the extension Ability. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](#uiextensionproxy)> | No | Callback for the asynchronous registration event. If this parameter is left empty, all asynchronous registration callbacks of the extension Ability are unsubscribed.<br> If it is not empty, the corresponding asynchronous registration callback is unsubscribed. |

### off('syncReceiverRegister')<sup>11+</sup>

off(type: 'syncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Used in the scenario where the component user unsubscribes from the synchronous registration event of the launched Ability after a connection is successfully established between the two parties. This method is used together with **on('syncReceiverRegister')** to cancel the subscription registered through **on('syncReceiverRegister')**. When it is no longer necessary to listen for the synchronous registration event (for example, before the component is destroyed), call this method to unsubscribe to avoid the callback being unable to be released.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type| Mandatory| Description|
| ------ | -------- | ----- | ------- |
| type   | string | Yes | Event type. The value is **'syncReceiverRegister'**, which indicates unsubscribing from the synchronous registration callback of the extension Ability. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](#uiextensionproxy)> | No | Callback for the synchronous registration event. If this parameter is left empty, it indicates unsubscribing from all callbacks triggered after the synchronous registration of the extension Ability.<br> If this parameter is not empty, it indicates unsubscribing from the corresponding synchronous registration callback. |

## Example

### Example 1: Loading a UIExtension

The **UIExtensionComponent** component can be used by both the host and provider. This example shows only the method used by the component and the UIExtensionAbility. For the code to run properly, you need to install the ability whose **bundleName** is **com.example.newdemo** and **abilityName** is **UIExtensionProvider** on the device.

**Component host**

The content of the user's entry page Index.ets is as follows:

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
  @State wid: number = 300;
  @State hei: number = 300;
  @State windowStrategy: WindowModeFollowStrategy = WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE;
  private proxy: UIExtensionProxy | null = null;
  private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params);
  private areaChangePlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(AreaChangePlaceholderBuilder), new Params);

  aboutToDisappear(): void {
    console.info('start do proxy off!');
    this.proxy?.off('syncReceiverRegister');
    this.proxy?.off('asyncReceiverRegister');
  }

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
            console.error(`onError: code = ${info.code}, message = ${info.message}`);
          })
          .onTerminated((info) => {
            console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
          })
          .onRemoteReady((proxy) => {
            console.info('onRemoteReady, for test');
            this.proxy = proxy;

            this.proxy.on("syncReceiverRegister", syncRegisterCallback1);

            this.proxy.on("asyncReceiverRegister", (proxy1) => {
              console.info('on invoke for test, type is asyncReceiverRegister');
            });
          })

        Button ("Send to UIExtensionAbility").onClick(() => {
          if (this.proxy != undefined) {
            this.proxy.send({data: "Hello 1"});

            try {
              let re = this.proxy.sendSync({data: "Hello 2"});
              console.info("for test, re=" + JSON.stringify(re));
            } catch (err) {
              console.error(`sendSync failed for test. Code: ${err.code}, message: ${err.message}`);
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
};

function syncRegisterCallback2(proxy: UIExtensionProxy) {
  console.info("on invoke for test, syncRegisterCallback2, type is syncReceiverRegister");
};
```

**Component provider**

The provider has three files that need to be modified:

- /src/main/ets/uiextensionability/UIExtensionProvider.ets

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

- Entry page file of the provider's extension Ability: **/src/main/ets/pages/extension.ets**

```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';

AppStorage.setOrCreate('message', 'UIExtensionAbility');

@Entry
@Component
struct Extension {
  @StorageLink('message') storageLink: string = '';
  private session: UIExtensionContentSession | undefined = undefined;
  pathStack: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === "hello") {
      PageOne();
    }
  }

  aboutToAppear() {
    this.session = this.getUIContext().getLocalStorage()?.get<UIExtensionContentSession>('session');
  }

  onPageShow() {
    if (this.session != undefined) {
      this.session.setReceiveDataCallback((data) => {
        this.storageLink = JSON.stringify(data);
        console.info("invoke for test, handle callback set by setReceiveDataCallback successfully");
      })

      this.session.setReceiveDataForResultCallback(onReceiveDataForResult);
    }
  }

  build() {
    Navigation(this.pathStack) {
      Row() {
        Column() {
          Text(this.storageLink)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          Button("Send to Component").onClick(() => {
            if (this.session != undefined) {
              this.session.sendData({"data": 543321});
              console.info('send 543321, for test');
            }
          })
          Button("terminate").onClick(() => {
            if (this.session != undefined) {
              this.session.terminateSelf();
            }
            this.getUIContext().getLocalStorage()?.clear();
          })
          Button("terminate with result").onClick(() => {
            if (this.session != undefined) {
              this.session.terminateSelfWithResult({
                resultCode: 0,
                want: {
                  bundleName: "myBundleName",
                  parameters: { "result": 123456 }
                }
              });
            }
            this.getUIContext().getLocalStorage()?.clear();
          })

          Button("Redirect").onClick(() => {
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
export struct PageOne {
  pathStack: NavPathStack = new NavPathStack();

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

function onReceiveDataForResult(data: Record<string, Object>): Record<string, Object> {
  let linkToMsg: SubscribedAbstractProperty<string> = AppStorage.link('message');
  linkToMsg.set(JSON.stringify(data));
  console.info("invoke for test, handle callback set by setReceiveDataForResultCallback successfully");
  return data;
}

```

- The provider's extension Ability. Add the corresponding configuration to the module configuration file **/src/main/module.json5**.

```json
{
    "name": "UIExtensionProvider",
    "srcEntry": "./ets/uiextensionability/UIExtensionProvider.ets",
    "description": "1",
    "label": "$string:EntryAbility_label",
    "type": "sys/commonUI",
    "exported": true
}
```

### Example 2: Isolating Scrolling Inside and Outside of UIExtensionComponent

This example demonstrates a scenario where both the **UIExtensionComponent** host and the UIExtensionAbility use [Scroll](ts-container-scroll.md) containers. By setting gesture interception on **UIExtensionComponent**, it achieves that external components do not respond to scrolling when the internal layer of the UIExtensionComponent is being scrolled.

Gesture usage:

Scrolling inside the component: scrolling within the component using touch gestures

Scrolling outside the component: scrolling of the outer container using the scrollbar

Before running, ensure that an ability whose **bundleName** is **com.example.newdemo** and **abilityName** as **UIExtensionProvider** is installed on the device.

The entry point file **UIExtensionProvider.ets** and the module configuration file **UIExtensionProvider.ets** are identical to those in [Example 1](#example-1-loading-a-uiextension).

The provider's extension Ability and module configuration file are the same as the module.json5 code of the extension module in [Example 1](#example-1-loading-a-uiextension).

- Example of the user's component usage:

```ts
@Entry
@Component
struct Second {
  @State message1: string = 'Hello World 1';
  @State message2: string = 'Hello World 2';
  @State message3: string = 'Hello World 3';
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
            }, (item: number) => item.toString())
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

- extension.ets (entry page file of the provider's UIExtensionAbility)

```ts
@Entry
@Component
struct Extension {
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
          }, (item: number) => item.toString())
        }
      }

    }
    .height('100%')
  }
}
```