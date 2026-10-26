# AutomationControlTargetResult (System API)

```TypeScript
interface AutomationControlTargetResult
```

Represents a target app and its automation control status with bundle name. Used as the return type of getAutomationControlTargets.

**Since:** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlTargetResult--><!--Device-abilityAccessCtrl-interface AutomationControlTargetResult-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the target app.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlTargetResult-bundleName: string--><!--Device-AutomationControlTargetResult-bundleName: string-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## status

```TypeScript
status: AutomationControlStatus
```

Automation control status.

**Type:** [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlTargetResult-status: AutomationControlStatus--><!--Device-AutomationControlTargetResult-status: AutomationControlStatus-End-->

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

<!--Device-AutomationControlTargetResult-targetTokenID: int--><!--Device-AutomationControlTargetResult-targetTokenID: int-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
