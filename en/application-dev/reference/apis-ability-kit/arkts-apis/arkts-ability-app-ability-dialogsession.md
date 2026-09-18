# @ohos.app.ability.dialogSession

The dialogSession module provides APIs related to the dialog box.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dialogSession } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getDialogSessionInfo](arkts-ability-dialogsession-getdialogsessioninfo-f-sys.md) | Obtains the session information based on the session ID. |
| [sendDialogResult](arkts-ability-dialogsession-senddialogresult-f-sys.md) | Sends a request for a dialog box. This API uses a promise to return the result. |
| [sendDialogResult](arkts-ability-dialogsession-senddialogresult-f-sys.md) | Sends a request for a dialog box. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DialogAbilityInfo](arkts-ability-dialogsession-dialogabilityinfo-i-sys.md) | Provides DialogAbility information, including the bundle name, module name, and ability name. |
| [DialogSessionInfo](arkts-ability-dialogsession-dialogsessioninfo-i-sys.md) | Provides session information, including the requester information, target ability information list, and other parameters. |
<!--DelEnd-->
