# InnerFullScreenLaunchComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @autojuan-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->

**InnerFullScreenLaunchComponent** is a component that allows the invoker to choose the timing for launching an atomic service. If the invoked app (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in full-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> To implement an embeddable atomic service within this component, it must inherit from [EmbeddableUIAbility](../../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md). If it does not inherit from **EmbeddableUIAbility**, the system cannot guarantee that the atomic service will function properly.


## Modules to Import

```ts
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```


## Child Components

Not supported

## Attributes
The [universal attributes](ts-component-general-attributes.md) are not supported.

## InnerFullScreenLaunchComponent

InnerFullScreenLaunchComponent({ content: Callback\<void>, controller: LaunchController, onReceive?: Callback<Record<string, Object>>, onError?: ErrorCallback, onTerminated?: Callback\<TerminationInfo> })

**Decorator**: [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator Type| Description|
| -------- | -------- | -------- | -------- | -------- |
| content | Callback\<void> | Yes| [\@BuilderParam](../../../ui/state-management/arkts-builderparam.md) | Content displayed in the component.|
| controller | [LaunchController](#launchcontroller) | Yes| - | Controller for launching the atomic service.|
| onReceive<sup>20+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record<string, Object>> | No| - | Callback triggered when an embedded atomic service calls [@ohos.window (window)](../arkts-apis-window.md) APIs.|
| onError<sup>23+</sup> | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | No| - | Callback triggered when an exception occurs during the execution of an embedded atomic service. You can obtain the error information based on the **code**, **name**, and **message** parameters in the callback and rectify the exception accordingly.|
| onTerminated<sup>23+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)> | No| - | Callback triggered when an embedded atomic service exits normally. Exit scenarios include user-triggered exit button taps or edge swipes, or calls to [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself).|
  
> **NOTE**
>
> Since API version 26.0.0, the **onTerminated** callback is triggered when an atomic service exits via an edge swipe gesture.

## LaunchController

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ---- | ---------- | ------ |------ | -- |
|launchAtomicService | [LaunchAtomicServiceCallback](#launchatomicservicecallback) | No| No| Launches an atomic service.|

## LaunchAtomicServiceCallback

type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void

Triggered when an atomic service is launched.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| --------------- | ------ |------ |------ |
|appId | string |Yes| App ID for the atomic service.|
| options | [AtomicServiceOptions](../../apis-ability-kit/js-apis-app-ability-atomicServiceOptions.md) | No| Parameters for launching the atomic service.|

## Events
The [universal events](ts-component-general-events.md) are not supported.

## Example

```ts
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';

@Entry
@Component
struct Index {

  @Builder
  ColumnChild() {
    Column() {
      Text('InnerFullScreenLaunchComponent').fontSize(16).margin({top: 100})
      Button('Start Sunrise/Sunset')
        .onClick(()=>{
          let appId1: string = '576****************';
          this.controller.launchAtomicService(appId1, {});
        }).height(30).width('50%').margin({top: 50})
      Button('Start Top-up')
        .onClick(()=>{
          let appId2: string = '576****************';
          this.controller.launchAtomicService(appId2, {});
        }).height(30).width('50%').margin({top: 50})
    }.backgroundColor(Color.Pink).height('100%').width('100%')
  }
  controller: LaunchController = new LaunchController();

  build() {
    Column() {
      InnerFullScreenLaunchComponent({
          content: this.ColumnChild,
          controller: this.controller,
          onReceive: (data) => {
            console.info("onReceive, data: " + data['ohos.atomicService.window']);
          },
          onError: (err: Error) => {
            console.error("onError, err: " + JSON.stringify(err));
          },
          onTerminated: (info: TerminationInfo) => {
            console.info("onTerminated, info: " + JSON.stringify(info));
          }
        })
    }
    .width('100%').height('100%')
  }
}

```
