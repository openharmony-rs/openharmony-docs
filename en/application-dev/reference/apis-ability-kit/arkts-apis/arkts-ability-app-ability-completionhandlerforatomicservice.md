# @ohos.app.ability.CompletionHandlerForAtomicService

**CompletionHandlerForAtomicService** is an optional parameter of
 [AtomicServiceOptions](arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) and is used to handle the
 result of an atomic service launch request.



## Modules to Import

```TypeScript
import { CompletionHandlerForAtomicService, FailureCode } from '@kit.AbilityKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CompletionHandlerForAtomicService](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md) | CompletionHandlerForAtomicService provides two callback functions, [onAtomicServiceRequestSuccess](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onatomicservicerequestsuccess) and [onAtomicServiceRequestFailure](arkts-ability-app-ability-completionhandlerforatomicservice-completionhandlerforatomicservice-c.md#onatomicservicerequestfailure), to handle the results of successful and failed atomic service launch requests, respectively. |

### Enums

| Name | Description |
| --- | --- |
| [FailureCode](arkts-ability-app-ability-completionhandlerforatomicservice-failurecode-e.md) | Enumerates the errors codes available for failures in launching an atomic service. |
