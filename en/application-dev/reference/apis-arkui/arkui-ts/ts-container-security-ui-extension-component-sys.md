# SecurityUIExtensionComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

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
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want) | Yes| Ability information to load. The **UIExtensionAbilit**y to be started is determined by both **bundleName** and **abilityName**. In addition, the **ability.want.params.uiExtensionType** field must be specified in **parameters** to indicate the type of the **UIExtensionAbility**. Currently, only **sysPicker/photoPicker** is supported.|
| options | [SecurityUIExtensionOptions](#securityuiextensionoptions) | No| Options used to construct **SecurityUIExtensionComponent**. If this parameter is left empty, the default value is used for each field.|

## SecurityUIExtensionOptions

Defines the options to be passed when constructing **SecurityUIExtensionComponent**.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| isTransferringCaller | boolean | No| Yes| Whether the **UIExtensionComponent** forwards the upper-level caller information when it is used for nesting.<br>**true**: yes; **false**: no.<br>The default value is **false**.|
| placeholder | [ComponentContent](../js-apis-arkui-ComponentContent.md#componentcontent-1) | No| Yes| Placeholder to be displayed before the **SecurityUIExtensionComponent** establishes a connection with the **UIExtensionAbility**.|
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
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[SecurityUIExtensionProxy](#securityuiextensionproxy)\> | Yes| Callback invoked to send data to the remote ability.|

### onReceive

onReceive(callback: Callback\<Record\<string, Object\>\>)

Triggered when the data sent by the started **UIExtensionAbility** is received. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record\<string, Object\>\> | Yes| Callback invoked to return the data received from the remote ability.|

### onError

onError(callback: ErrorCallback)

Triggered when an exception occurs during the running of the started ability extension, excluding the scenario where the **UIExtensionAbility** is disconnected. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes| Callback used to receive exception information.|

### onTerminated

onTerminated(callback: Callback\<TerminationInfo>)

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
| code | number | No| No| Result code returned when the **UIExtensionAbility** exits. The value **0** indicates that the **UIExtensionAbility** exits normally, and a non-zero value indicates that the **UIExtensionAbility** exits abnormally. The meaning of the result code is defined by the **UIExtensionAbility** that is started.|
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md#want) | No| Yes| Data returned when the **UIExtensionAbility** exits.|

## SecurityUIExtensionProxy

Implements a **SecurityUIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started ability through the connection established between the two parties.

### send

send(data: Record\<string, Object\>): void

Asynchronously sends data to the ability started by the component host through the connection established between the two parties.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | Yes| Data to be asynchronously sent to the started **UIExtensionAbility**.|

### sendSync

sendSync(data: Record\<string, Object\>): Record\<string, Object\>

Synchronously sends data to the ability started by the component host through the connection established between the two parties.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | Record\<string, Object\> | Yes| Data to be synchronously sent to the started **UIExtensionAbility**.|

**Return value**

| Type| Description|
| -------- | -------- |
| Record\<string, Object\> | Data returned by the extension ability.|

**Error codes**

For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

| ID| Error Message|
| -------- | -------- |
| 100011 | No callback has been registered to respond to this request. |
| 100012 | Transferring data failed. |

### on('asyncReceiverRegister')

on(type: 'asyncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

Subscribes to the callback triggered for asynchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| The value is fixed to **asyncReceiverRegister**, indicating a subscription to the callback triggered for asynchronous registration of the extended ability.|
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | Yes|  Callback triggered after the extension ability registers a [setReceiveDataCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedatacallback).|

### on('syncReceiverRegister')

on(type: 'syncReceiverRegister', callback: Callback\<UIExtensionProxy\>): void

Subscribes to the callback triggered for synchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| The value is fixed to **syncReceiverRegister**, indicating subscription to the asynchronous registration of the extension ability.|
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | Yes|  Callback triggered after the extension ability registers a [setReceiveDataForResultCallback](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession-sys.md#setreceivedataforresultcallback11).|

### off('asyncReceiverRegister')

off(type: 'asyncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from the callback triggered for the asynchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| The value is fixed to **asyncReceiverRegister**, indicating unsubscription from the callback triggered for asynchronous registration of the extended ability.|
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | No| Callback function. If this parameter is left empty, it means unsubscribing from all callbacks triggered after **UIExtensionAbility**'s asynchronous registration. If this parameter is not empty, it means unsubscribing from callbacks corresponding to **type**.|

### off('syncReceiverRegister')

off(type: 'syncReceiverRegister', callback?: Callback\<UIExtensionProxy\>): void

Unsubscribes from the callback triggered for the synchronous registration of the started ability. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| The value is fixed to **syncReceiverRegister**, indicating unsubscription to the asynchronous registration of the extension ability.|
| callback | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[UIExtensionProxy](../../apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#uiextensionproxy)\> | No| Callback to unsubscribe from. If this parameter is left empty, it means unsubscribing from all callbacks triggered after **UIExtensionAbility**'s synchronous registration.|

## Examples

### Example 1: Basic Usage of SecurityUIExtensionComponent

This example demonstrates the basic usage of **SecurityUIExtensionComponent**. It shows how to start the **UIExtensionAbility** of a specified ability by configuring **Want**, and how to obtain error information through the **onError** callback when a connection exception occurs.

Since API version 26.0.0, the [onError](#onerror) event is added.

``` TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  @State want: Want = {
    bundleName: 'com.ohos.myapplication',
    abilityName: 'SUIExtensionProvider',
    parameters: {
      'ability.want.params.uiExtensionType': 'sysPicker/photoPicker',
    },
  }

  build() {
    Column() {
      Button('top')
        .width('80%')
        .height(40)
        .margin(3)

      SecurityUIExtensionComponent(this.want)
        .width('90%')
        .height('90%').backgroundColor(Color.Green)
        .onError((error: BusinessError) => {
          this.message = 'Error: ' + JSON.stringify(error);
          hilog.info(0x0000, 'SecurityUIExtensionComponentDemo', this.message);
        })

      Button('bottom')
        .width('80%')
        .height(40)
        .margin(3)
    }
    .height('90%')
    .width('90%')
  }
}
```
