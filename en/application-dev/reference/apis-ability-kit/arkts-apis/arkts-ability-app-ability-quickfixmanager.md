# @ohos.app.ability.quickFixManager(quickFixManager)

The quickFixManager module provides APIs for quick fix. With quick fix, you can fix bugs in your application by applying patches, which is more efficient than by updating the entire application.

**Since:** 9

<!--Device-unnamed-declare namespace quickFixManager--><!--Device-unnamed-declare namespace quickFixManager-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [applyQuickFix](arkts-ability-quickfixmanager-applyquickfix-f-sys.md#applyquickfix1) | Applies a quick fix patch. This API uses an asynchronous callback to return the result. |
| [applyQuickFix](arkts-ability-quickfixmanager-applyquickfix-f-sys.md#applyquickfix2) | Applies a quick fix patch. This API uses a promise to return the result. |
| [getApplicationQuickFixInfo](arkts-ability-quickfixmanager-getapplicationquickfixinfo-f-sys.md#getapplicationquickfixinfo1) | Obtains the quick fix information of the application. This API uses an asynchronous callback to return the result. |
| [getApplicationQuickFixInfo](arkts-ability-quickfixmanager-getapplicationquickfixinfo-f-sys.md#getapplicationquickfixinfo2) | Obtains the quick fix information of the application. This API uses a promise to return the result. |
| [revokeQuickFix](arkts-ability-quickfixmanager-revokequickfix-f-sys.md#revokequickfix1) | Revokes quick fix. This API uses an asynchronous callback to return the result. |
| [revokeQuickFix](arkts-ability-quickfixmanager-revokequickfix-f-sys.md#revokequickfix2) | Revokes quick fix. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ApplicationQuickFixInfo](arkts-ability-quickfixmanager-applicationquickfixinfo-i-sys.md) | Defines the quick fix information at the application level. |
| [HapModuleQuickFixInfo](arkts-ability-quickfixmanager-hapmodulequickfixinfo-i-sys.md) | Defines the quick fix information at the HAP file level. |
<!--DelEnd-->
