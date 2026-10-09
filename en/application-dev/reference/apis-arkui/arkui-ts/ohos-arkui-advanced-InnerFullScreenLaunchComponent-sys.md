# InnerFullScreenLaunchComponent (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @autojuan-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=0bd491b8a12cab22cb29f482eaab85583a7b686e translatedAt=2026-08-28T01:32:41.628Z pushedAt=2026-08-28T06:12:06.126Z -->

A component that launches an atomic service in non-explicit full-screen mode. The invoker can choose the timing for launching the atomic service. When the invoked party authorizes the invoker to run the atomic service in embedded mode, the invoker runs the atomic service in full-screen embedded mode; otherwise, the invoker launches the atomic service in a pop-up manner.

> **NOTE**
>
> This component is supported since API version 12. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> To implement an atomic service that can run in embedded mode in this component, the atomic service must inherit from [EmbeddableUIAbility](../../apis-ability-kit/js-apis-app-ability-embeddableUIAbility.md). If it does not inherit from EmbeddableUIAbility, the system cannot guarantee that the atomic service functions properly.

## Modules to Import

```ts
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## Events

The [universal events](ts-component-general-events.md) are not supported.

## InnerFullScreenLaunchComponent

InnerFullScreenLaunchComponent({ content: Callback\<void>, controller: LaunchController, onReceive?: Callback\<Record<string, Object>>, onError?: ErrorCallback, onTerminated?: Callback\<TerminationInfo> })

**Decorator:** [@Component](../../../ui/state-management/arkts-create-custom-components.md#component)

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator Type| Description|
| -------- | -------- | -------- | -------- | -------- |
| content | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<void> | Yes | [@BuilderParam](../../../ui/state-management/arkts-builderparam.md) | Content displayed by the component. |
| controller | [LaunchController](#launchcontroller) | Yes| - | Controller for launching the atomic service.|
| onReceive<sup>20+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<Record<string, Object>> | No | - | Callback invoked when the launched atomic service in embedded running mode calls related APIs through [@ohos.window (Window)](../arkts-apis-window.md). |
| onError<sup>23+</sup> | [ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | No| - | Callback triggered when an exception occurs during the execution of an embedded atomic service. You can obtain the error information based on the **code**, **name**, and **message** parameters in the callback and rectify the exception accordingly.|
| onTerminated<sup>23+</sup> | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](ts-container-embedded-component.md#terminationinfo)> | No | - | Callback invoked when the launched atomic service in embedded running mode exits normally by tapping the exit button of the atomic service, swiping sideways, or calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself). |

> **NOTE**
>
> - If the atomic service exits by calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateselfwithresult), the information it carries is passed to the input parameter of the callback.
> - If the atomic service exits by calling [terminateSelf](../../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#terminateself), in the input parameter of the callback, "code" takes the default value "0" and "want" is "undefined".
> - Since API version 26.0.0, the **onTerminated** callback is triggered when the atomic service exits through a side-swipe gesture.

## LaunchController

Controller for launching an atomic service.

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
| options | [AtomicServiceOptions](../../apis-ability-kit/js-apis-app-ability-atomicServiceOptions.md) | No | Parameters for launching the atomic service. If this parameter is not set, the default parameters are used to launch the atomic service. |

## Example

> **NOTE**
>
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:  
> 1. Open the HiLog panel in DevEco Studio.  
> 2. Switch the mode in the upper left corner to User logs of selected app.  
> 3. In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").

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
        .onClick(() => {
          let appId1: string = '576****************';
          this.controller.launchAtomicService(appId1, {});
        }).height(30).width('50%').margin({top: 50})
      Button('Start Top-up')
        .onClick(() => {
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
            console.info('onReceive, data: ' + JSON.stringify(data['ohos.atomicService.window']));
          },
          onError: (err: BusinessError) => {
            console.error(`onError, code: ${err.code}, message: ${err.message}`);
          },
          onTerminated: (info: TerminationInfo) => {
            console.info('onTerminated, info: ' + JSON.stringify(info));
          }
        })
    }
    .width('100%').height('100%')
  }
}

```