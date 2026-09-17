# InnerFullScreenLaunchComponent (System API)

**InnerFullScreenLaunchComponent** is a component that allows the invoker to choose the timing for launching an atomic service. If the invoked app (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in full-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner.

> **NOTE:** 
> 
> To implement an embeddable atomic service within this component, it must inherit from
> [EmbeddableUIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md). If it does not inherit from
> **EmbeddableUIAbility**, the system cannot guarantee that the atomic service will function properly.

**Since:** 12

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```

## content

```TypeScript
content: Callback<void>
```

Content displayed in the component.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt;

**Since:** 12

**Decorator:** @BuilderParam

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## controller

```TypeScript
controller: LaunchController
```

Controller for launching the atomic service.

**Type:** [LaunchController](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-launchcontroller-c-sys.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onError

```TypeScript
onError?: ErrorCallback
```

Callback triggered when an exception occurs during the execution of an embedded atomic service. You can obtain the error information based on the **code**, **name**, and **message** parameters in the callback and rectify the exception accordingly.

**Type:** [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md)

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onReceive

```TypeScript
onReceive?: Callback<Record<string, Object>>
```

Callback triggered when an embedded atomic service calls [@ohos.window (window)](arkts-arkui-window-n.md) APIs.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt;

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onTerminated

```TypeScript
onTerminated?: Callback<TerminationInfo>
```

Callback triggered when an embedded atomic service exits normally. Exit scenarios include user-triggered exit button taps or edge swipes, or calls to terminateSelfWithResult or terminateSelf.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TerminationInfo](../arkts-components/arkts-arkui-terminationinfo-i.md)&gt;

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
