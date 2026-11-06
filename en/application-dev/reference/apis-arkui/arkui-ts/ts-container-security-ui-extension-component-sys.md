# SecurityUIExtensionComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-19T07:17:20.536Z pushedAt=2026-08-20T10:45:03.050Z -->

**SecurityUIExtensionComponent** is used to embed the UI provided by another application on the current page. The displayed content runs in another process, and the current application does not participate in its layout and rendering.

It is typically used in modular development scenarios that require process isolation. Currently, **SecurityUIExtensionComponent** can only start **UIExtensionAbility** of the [PhotoPicker](../../apis-media-library-kit/ohos-file-PhotoPickerComponent.md) type.

> **NOTE**
>
> - The APIs provided by this module are system APIs.
>
> - The APIs of this module can be used only in the stage model.

**Since:** 26.0.0

## Child Components

None

## APIs

SecurityUIExtensionComponent(want: Want, options?: SecurityUIExtensionOptions)

Creates a **SecurityUIExtensionComponent** component to embed and display the UI provided by a remote [UIExtensionAbility](../../apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md).

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want) | Yes| Ability information to load. The **UIExtensionAbility** to be started is determined by both **bundleName** and **abilityName**. In addition, the **ability.want.params.uiExtensionType** field must be specified in **parameters** to indicate the type of the **UIExtensionAbility**. Currently, only **sysPicker/photoPicker** is supported.|
| options | [SecurityUIExtensionOptions](#securityuiextensionoptions) | No| Options used to construct **SecurityUIExtensionComponent**. If this parameter is left empty, the default value is used for each field.|

## SecurityUIExtensionOptions

Defines the options to be passed when constructing **SecurityUIExtensionComponent**.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| isTransferringCaller | boolean | No | Yes | Whether to forward the Caller information of the upper-level caller (that is, the identity information of the **Ability** that initiates the call) when **SecurityUIExtensionComponent** is nested, so as to support call chain passing in multi-level nesting scenarios.<br>**true**: forwards the Caller information of the upper level; **false**: does not forward the Caller information of the upper level.<br>Default value: **false** |
| placeholder | [ComponentContent](../js-apis-arkui-ComponentContent.md#componentcontent-1) | No | Yes | Placeholder displayed before the connection between **SecurityUIExtensionComponent** and the **UIExtensionAbility** is established. No placeholder is displayed if this attribute is not set. |
| dpiFollowStrategy | [SecurityDpiFollowStrategy](#securitydpifollowstrategy) | No| Yes| Resolution following strategy for **SecurityUIExtensionComponent**, used to control whether the embedded **UIExtensionAbility** content follows the host application's resolution or uses its own resolution.<br>Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**|

## SecurityDpiFollowStrategy

Defines the enum of the resolution following strategy for **SecurityUIExtensionComponent**.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| FOLLOW_HOST_DPI | 0 | The resolution follows the host application.|
| FOLLOW_UI_EXTENSION_ABILITY_DPI | 1 | The resolution follows the **UIExtensionAbility**.|

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The following events are supported:

### onRemoteReady

onRemoteReady(callback: Callback\<SecurityUIExtensionProxy\>)

Triggered when the **UIExtensionAbility** connection is complete. This API uses an asynchronous callback to return the result. You can then use the returned [SecurityUIExtensionProxy](#securityuiextensionproxy) to send data to the started ability.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | Yes | Callback whose input parameter is **SecurityUIExtensionProxy**, which can be used to send data to the peer **Ability** and subscribe to events. |

### onReceive

onReceive(callback: Callback\<Record\<string, Object\>\>)

Triggered when the data sent by the started **UIExtensionAbility** is received. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\> | Yes | Callback invoked to return the data received from the peer **Ability**. The data is a **Record<string, Object>** key-value pair, and the specific fields are customized by the sender (the launched Ability) through the **sendData** method. |

### onError

onError(callback: ErrorCallback)

Callback triggered when an exception occurs during the running of the launched **UIExtensionAbility**. This does not include the scenario where the connection to the **UIExtensionAbility** is disconnected. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback used to receive exception information.|

### onTerminated

onTerminated(callback: Callback\<TerminationInfo\>)

Triggered when the started **UIExtensionAbility** exits normally by calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself). This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](#terminationinfo)\> | Yes| Callback function, which is used to receive the result returned by **UIExtensionAbility**.|

## TerminationInfo

Defines the result returned when the started **UIExtensionAbility** exits normally.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| code | number | No | No | Result code returned when the launched **UIExtensionAbility** exits. The value **0** indicates normal exit, and a non-zero value indicates abnormal exit. The specific meaning of the result code is defined by the launched **UIExtensionAbility**. |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want) | No | Yes | Data returned when the launched **UIExtensionAbility** exits. This field is empty if no data is returned. |

## SecurityUIExtensionProxy

Used to send data to the launched **Ability** and subscribe to and unsubscribe from event callbacks after a successful connection is established.

**Since**: 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### send

send(data: Record\<string, Object\>): void

Used to send data to the launched **Ability** after a successful connection is established, providing asynchronous sending capability. The data will be received and processed by the extension **Ability** through [setReceiveDataCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedatacallback).

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | Yes | Data asynchronously sent to the launched **Ability**. |

### sendSync

sendSync(data: Record\<string, Object\>): Record\<string, Object\>

Sends data to the launched **Ability** after a successful connection is established. The data will be processed by the launched **Ability** through **setReceiveDataForResultCallback** and the result will be returned.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | Yes | Data synchronously sent to the launched **Ability**. |

**Return value**

| Type| Description|
| -------- | -------- |
| Record\<string, Object\> | Response data returned by the launched **Ability** after processing the synchronous send request. |

**Error codes**

For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

| ID| Error Message|
| -------- | -------- |
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')

on(type: 'asyncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

After a successful connection is established, subscribes to the callback triggered when the launched **Ability** performs asynchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **'asyncReceiverRegister'**, which indicates the callback triggered when the launched **Ability** performs asynchronous registration. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | Yes | Callback triggered after the launched **Ability** registers [setReceiveDataCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedatacallback). |

### on('syncReceiverRegister')

on(type: 'syncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

After a successful connection is established, subscribes to the callback triggered when the launched **Ability** performs synchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Mandatory | Fixed value **'syncReceiverRegister'**, which indicates the callback triggered when the launched **Ability** performs synchronous registration. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | Mandatory | Callback function. Callback triggered after the launched **Ability** registers [setReceiveDataForResultCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedataforresultcallback11). |

### off('asyncReceiverRegister')

off(type: 'asyncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from the callback triggered when the launched **Ability** performs asynchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **'asyncReceiverRegister'**, used to unsubscribe from the callback triggered when the launched **Ability** performs asynchronous registration. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | No | Callback function. If this parameter is left empty, all callbacks for asynchronous registration are unsubscribed. If it is not empty, the specified callback for asynchronous registration is unsubscribed. |

### off('syncReceiverRegister')

off(type: 'syncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from the callback triggered when the launched **Ability** performs synchronous registration. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes | Fixed value **'syncReceiverRegister'**, used to unsubscribe from the callback triggered when the launched **Ability** performs synchronous registration. |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | No | Callback function. If it is empty, unsubscribes from all synchronously registered callbacks. If it is not empty, unsubscribes from the specified synchronously registered callback. |

## Examples

### Example 1: Launching a Remote UIExtensionAbility and Performing Bidirectional Data Communication Using SecurityUIExtensionComponent

This example demonstrates how to use **SecurityUIExtensionComponent**, including launching a specified **UIExtensionAbility** by configuring [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want), obtaining [SecurityUIExtensionProxy](#securityuiextensionproxy) through [onRemoteReady](#onremoteready), sending data using [send](#send) or [sendSync](#sendsync), and handling events through callbacks such as [onReceive](#onreceive), [onError](#onerror), and [onTerminated](#onterminated).

Since API version 26.0.0, the [onRemoteReady](#onremoteready), [onReceive](#onreceive), [onError](#onerror), and [onTerminated](#onterminated) events are added.

**Component consumer**

``` TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @State receiveData: string = '';
  private want: Want = {
    bundleName: 'com.example.securityUIExtProvider',
    abilityName: 'SecurityUIExtProvider',
    parameters: {
      'ability.want.params.uiExtensionType': 'sysPicker/photoPicker',
    },
  };
  private proxy: SecurityUIExtensionProxy | null = null;

  build() {
    Column() {
      Text(this.message).fontSize(20).margin(10)
      Text('Data received: ' + this.receiveData).fontSize(16).margin(10)

      SecurityUIExtensionComponent(this.want)
        .width('90%')
        .height('60%')
        .backgroundColor(Color.Green)
        .onRemoteReady((proxy: SecurityUIExtensionProxy) => {
          hilog.info(0x0000, 'SUECDemo', 'onRemoteReady');
          this.proxy = proxy;

          this.proxy.on('asyncReceiverRegister', asyncRegisterCallback);
          this.proxy.on('syncReceiverRegister', syncRegisterCallback);
        })
        .onReceive((data: Record<string, Object>) => {
          this.receiveData = JSON.stringify(data['data']);
          hilog.info(0x0000, 'SUECDemo', 'onReceive: ' + this.receiveData);
        })
        .onError((error: BusinessError) => {
          this.message = `Error: ${JSON.stringify(error)}`;
          hilog.error(0x0000, 'SUECDemo', `onError. Code: ${error.code}, message: ${error.message}`);
        })
        .onTerminated((info: TerminationInfo) => {
          hilog.info(0x0000, 'SUECDemo', 'onTerminated: code=' + info.code);
        })

      Button('Send Async Data')
        .margin(5)
        .onClick(() => {
          if (this.proxy) {
            this.proxy.send({ data: 'Async message from the consumer' });
          }
        })

      Button('Send Sync Data')
        .margin(5)
        .onClick(() => {
          if (this.proxy) {
            try {
              let result = this.proxy.sendSync({ data: 'Sync message from the consumer' });
              hilog.info(0x0000, 'SUECDemo', 'sendSync result: ' + JSON.stringify(result));
            } catch (err) {
              hilog.error(0x0000, 'SUECDemo', `sendSync failed. Code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
            }
          }
        })


      Button('Unregister Sync Listener')
        .margin(5)
        .onClick(() => {
          if (this.proxy) {
            this.proxy.off('syncReceiverRegister');
            hilog.info(0x0000, 'SUECDemo', `offSyncReceiverRegister`);
          }
        })

      Button('Unregister Async Listener')
        .margin(5)
        .onClick(() => {
          if (this.proxy) {
            this.proxy.off('asyncReceiverRegister');
            hilog.info(0x0000, 'SUECDemo', `offAsyncReceiverRegister`);
          }
        })
    }
    .height('90%')
    .width('90%')
  }
}


const asyncRegisterCallback = (proxy: UIExtensionProxy) => {
  hilog.info(0x0000, 'SUECDemo', 'onAsyncReceiverRegister');
};

const syncRegisterCallback = (proxy: UIExtensionProxy) => {
  hilog.info(0x0000, 'SUECDemo', 'onSyncReceiverRegister');
};
```

**Component provider**

The provider needs to modify the following three files.

- The provider adds the extension entry file `/src/main/ets/uiextensionability/SecurityUIExtProvider.ets`.

  ```ts
  import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  const TAG: string = '[SecurityUIExtAbility]';
  
  export default class SecurityUIExtProvider extends UIExtensionAbility {
    onCreate() {
      hilog.info(0x0000, TAG, 'onCreate');
    }
  
    onForeground() {
      hilog.info(0x0000, TAG, 'onForeground');
    }
  
    onBackground() {
      hilog.info(0x0000, TAG, 'onBackground');
    }
  
    onDestroy() {
      hilog.info(0x0000, TAG, 'onDestroy');
    }
  
    onSessionCreate(want: Want, session: UIExtensionContentSession) {
      hilog.info(0x0000, TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
      let param: Record<string, UIExtensionContentSession> = {
        'session': session
      };
      let storage: LocalStorage = new LocalStorage(param);
      try {
        session.loadContent('pages/SecurityExtension', storage);
      } catch (error) {
        hilog.error(0x0000, TAG, `onSessionCreate loadContent failed. Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
      }
    }
  
    onSessionDestroy(session: UIExtensionContentSession) {
      hilog.info(0x0000, TAG, 'onSessionDestroy');
    }
  }
  ```

- The provider adds the extension **Ability** entry page file `/src/main/ets/pages/SecurityExtension.ets`.

  ```ts
  import { UIExtensionContentSession } from '@kit.AbilityKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  let storage = LocalStorage.getShared();
  AppStorage.setOrCreate('message', 'UIExtensionAbility');
  
  @Entry(storage)
  @Component
  struct SecurityExtension {
    @StorageLink('message') storageLink: string = '';
    private session: UIExtensionContentSession | undefined = storage.get<UIExtensionContentSession>('session');
  
    build() {
      Scroll() {
        Column() {
          Text(this.storageLink)
            .fontSize(10)
            .fontWeight(FontWeight.Bold)
            .width('80%')
            .height('10%')
  
          Button('Click to send data to Component')
            .fontSize(12)
            .width('80%')
            .height('10%')
            .margin(1)
            .onClick(() => {
              hilog.info(0x0000, 'SecurityExtension', 'send 543321, for test start');
              if (this.session != undefined) {
                this.session.sendData({ 'data': 'Data that Component should receive' });
                hilog.info(0x0000, 'SecurityExtension', 'send for test');
              }
            })
  
          Button('terminate')
            .fontSize(12)
            .width('80%')
            .height('10%')
            .margin(1)
            .onClick(() => {
              hilog.info(0x0000, 'SecurityExtension', 'terminate');
              if (this.session != undefined) {
                this.session.terminateSelf();
              }
              storage.clear();
            })
  
          Button('terminate with result')
            .fontSize(12)
            .width('80%')
            .height('10%')
            .margin(1)
            .onClick(() => {
              hilog.info(0x0000, 'SecurityExtension', 'terminateSelfWithResult');
              if (this.session != undefined) {
                this.session.terminateSelfWithResult({
                  resultCode: 0,
                  want: {
                    bundleName: 'myBundleName',
                    parameters: { 'result': 123456 }
                  }
                });
              }
              storage.clear();
            })

          Button('setReceiveDataCallback')
            .fontSize(12)
            .width('80%')
            .height('10%')
            .margin(1)
            .onClick(() => {
              this.session?.setReceiveDataCallback((data) => {
                this.storageLink = JSON.stringify(data);
                hilog.info(0x0000, 'SecurityExtension', 'test setReceiveDataCallback successfully: ' + this.storageLink);
              })
            })
  
          Button('setReceiveDataForResultCallback')
            .fontSize(12)
            .width('80%')
            .height('10%')
            .margin(1)
            .onClick(() => {
              this.session?.setReceiveDataForResultCallback(receiveDataForResultCallback);
            })
        }
      }
      .id('providerScroll')
      .width('100%')
      .height('100%')
    }
  }
  
  const receiveDataForResultCallback = (data: Record<string, Object>): Record<string, Object> => {
    let linkToMsg: SubscribedAbstractProperty<string> = AppStorage.link('message');
    linkToMsg.set(JSON.stringify(data));
    hilog.info(0x0000, 'SecurityExtension',
      'invoke for test, handle callback set by setReceiveDataForResultCallback successfully');
    return data;
  }
  ```

- Provider module.json5 configuration.

  ```json
  "extensionAbilities": [
        {
          "name": "SecurityUIExtProvider",
          "srcEntry": "./ets/uiextensionability/SecurityUIExtProvider.ets",
          "description": "$string:module_desc",
          "label": "$string:EntryAbility_desc",
          "type": "sysPicker/photoPicker",
          "exported": true,
          "metadata" : [{
            "name" : "supportUIInteraction",
            "value": "false"
          }]
        }
      ]
  ```