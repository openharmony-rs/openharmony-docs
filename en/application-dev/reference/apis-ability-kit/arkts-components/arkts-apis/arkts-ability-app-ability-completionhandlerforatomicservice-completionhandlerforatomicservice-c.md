# CompletionHandlerForAtomicService

```TypeScript
declare class CompletionHandlerForAtomicService
```

CompletionHandlerForAtomicService provides two callback functions, [onAtomicServiceRequestSuccess](#onatomicservicerequestsuccess) and [onAtomicServiceRequestFailure](#onatomicservicerequestfailure), to handle the results of successful and failed atomic service launch requests, respectively.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
```

## onAtomicServiceRequestFailure

```TypeScript
onAtomicServiceRequestFailure(appId: string, failureCode: FailureCode, failureMessage: string): void
```

Called when the atomic service fails to be launched.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId of the target atomic service. |
| failureCode | [FailureCode](arkts-ability-app-ability-completionhandlerforatomicservice-failurecode-e.md) | Yes | Error code of the failure cause. |
| failureMessage | string | Yes | Description of the failure cause. |

**Examples**

For details, see CompletionHandlerForAtomicService Usage Example.

## onAtomicServiceRequestSuccess

```TypeScript
onAtomicServiceRequestSuccess(appId: string): void
```

Called when the atomic service is successfully launched.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId of the target atomic service. |

**Examples**

For details, see CompletionHandlerForAtomicService Usage Example.
