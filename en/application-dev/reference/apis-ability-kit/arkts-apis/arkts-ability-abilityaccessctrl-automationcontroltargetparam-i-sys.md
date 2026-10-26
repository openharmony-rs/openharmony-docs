# AutomationControlTargetParam (System API)

```TypeScript
interface AutomationControlTargetParam
```

Represents a target app and its automation control status.

**Since:** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlTargetParam--><!--Device-abilityAccessCtrl-interface AutomationControlTargetParam-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## status

```TypeScript
status: AutomationControlStatus
```

Automation control status.

**Type:** [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlTargetParam-status: AutomationControlStatus--><!--Device-AutomationControlTargetParam-status: AutomationControlStatus-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## targetTokenID

```TypeScript
targetTokenID: number
```

Token ID of the target app.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlTargetParam-targetTokenID: int--><!--Device-AutomationControlTargetParam-targetTokenID: int-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
