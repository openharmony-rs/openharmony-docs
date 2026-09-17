# @ohos.app.ability.CompletionHandlerForAbilityStartCallback

**CompletionHandlerForAbilityStartCallback** is an optional parameter of
 AbilityStartCallback. It provides callback results for launching ability
 components of specific types through the vertical panel.



## Modules to Import

```TypeScript
import { CompletionHandlerForAbilityStartCallback, AbilityStartFailureCode } from '@kit.AbilityKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CompletionHandlerForAbilityStartCallback](arkts-ability-app-ability-completionhandlerforabilitystartcallback-completionhandlerforabilitystartcallback-c.md) | CompletionHandlerForAbilityStartCallback provides two callback functions, **onRequestSuccess** and **onRequestFailure**, which are invoked when launching the specified ability succeeds or fails, respectively. |

### Enums

| Name | Description |
| --- | --- |
| [AbilityStartFailureCode](arkts-ability-app-ability-completionhandlerforabilitystartcallback-abilitystartfailurecode-e.md) | Enumerates the specific error codes for ability launch failures. |

### Types

| Name | Description |
| --- | --- |
| [OnRequestFailureFn](arkts-ability-onrequestfailurefn-t.md) | Defines the callback for failed ability launches. |
| [OnRequestSuccessFn](arkts-ability-onrequestsuccessfn-t.md) | Defines the callback for successful ability launches. |
