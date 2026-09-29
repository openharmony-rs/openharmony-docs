# CompletionHandlerForAbilityStartCallback

```TypeScript
export class CompletionHandlerForAbilityStartCallback
```

CompletionHandlerForAbilityStartCallback provides two callback functions, **onRequestSuccess** and **onRequestFailure**, which are invoked when launching the specified ability succeeds or fails, respectively.

**Since:** 21

<!--Device-unnamed-export class CompletionHandlerForAbilityStartCallback--><!--Device-unnamed-export class CompletionHandlerForAbilityStartCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { CompletionHandlerForAbilityStartCallback, AbilityStartFailureCode } from '@kit.AbilityKit';
```

## onRequestFailure

```TypeScript
onRequestFailure?: OnRequestFailureFn
```

Callback invoked when launching the specified ability fails.

This API can be used in atomic services since API version 21.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-CompletionHandlerForAbilityStartCallback-onRequestFailure?: OnRequestFailureFn--><!--Device-CompletionHandlerForAbilityStartCallback-onRequestFailure?: OnRequestFailureFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onRequestSuccess

```TypeScript
onRequestSuccess?: OnRequestSuccessFn
```

Callback invoked when the specified ability is successfully launched.

This API can be used in atomic services since API version 21.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-CompletionHandlerForAbilityStartCallback-onRequestSuccess?: OnRequestSuccessFn--><!--Device-CompletionHandlerForAbilityStartCallback-onRequestSuccess?: OnRequestSuccessFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
