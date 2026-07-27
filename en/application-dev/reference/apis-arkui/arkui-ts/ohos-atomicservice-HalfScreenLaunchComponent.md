# HalfScreenLaunchComponent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @autojuan-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->

**HalfScreenLaunchComponent** is a component designed for launching atomic services in half screen. If the invoked application (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in half-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner.

> **NOTE**
>
> This component is supported since API version 18. Updates will be marked with a superscript to indicate their earliest API version.
>
> To implement an embeddable atomic service, make sure it inherits from [EmbeddableUIAbility](../../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md). If the atomic service does not inherit from **EmbeddableUIAbility**, the system cannot guarantee its proper operation.

## Modules to Import

```ts
import { HalfScreenLaunchComponent } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes
The [universal attributes](ts-component-general-attributes.md) are not supported.

## HalfScreenLaunchComponent

HalfScreenLaunchComponent({ content: Callback\<void>, appId: string, options?: AtomicServiceOptions, onError?: ErrorCallback, onTerminated?: Callback\<TerminationInfo>, onReceive?: Callback<Record<string, Object>> })

**Decorator**: [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator| Description|
| -------- | -------- | -------- | -------- | -------- |
| content | Callback\<void> | Yes| [\@BuilderParam](../../../ui/state-management/arkts-builderparam.md) | Content displayed in the component.|
| appId | string | Yes| - | Application ID for the atomic service.|
| options | [AtomicServiceOptions](../../apis-ability-kit/js-apis-app-ability-atomicServiceOptions.md) | No| - | Parameters for starting the atomic service. The default value is empty.|
| onError |[ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | No| - | Invoked when an error occurs during the running of the atomic service.|
| onTerminated | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)> | No| - | Callback triggered when an embedded atomic service exits normally. Exit scenarios include user-triggered exit button taps or edge swipes, or calls to [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself).|
| onReceive<sup>20+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record<string, Object>> | No| - | Callback triggered when an embedded atomic service calls [@ohos.window (window)](../arkts-apis-window.md) APIs.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## Example

This example demonstrates how to start a top-up service in embedded mode.

> **NOTE**
>
>Embedded atomic services run in separate processes, so their crashes and exceptions are not visible directly in the host's logs. Follow the steps below to view the complete error stack trace during local debugging: 
>1. Open the HiLog panel in DevEco Studio. 
>2. Switch the mode in the top-left corner to **User logs of selected app**. 
>3. In the process list on the right, select the process of the launched atomic service. The package name has **embeddable** within its suffix segment.

```ts
import { HalfScreenLaunchComponent } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  appId: string = "576****************"; // Application ID for the atomic service.

  build() {
    Column() {
      HalfScreenLaunchComponent({
        appId: this.appId,
        options: {},
        onTerminated:  (info:TerminationInfo)=> {
          console.info('onTerminated info = '+ info.want);
        },
        onError: (err) => {
          console.error(" onError code: " + err.code + ", message: ", err.message);
        },
        onReceive: (data) => {
          console.info("onReceive, data: " + data['ohos.atomicService.window']);
        }
      }) {
        Column() {
          Image($r('app.media.app_icon'))
          Text('Start top-up')
        }.width("80vp").height("80vp").margin({bottom:30})
      } // Pass content through the trailing closure.
    }
  }

}
```
