# ControlAppStatusResult

```TypeScript
interface ControlAppStatusResult
```

Control permission status result for an application.

**Since:** 26.1.0

<!--Device-abilityToolAccessCtrl-interface ControlAppStatusResult--><!--Device-abilityToolAccessCtrl-interface ControlAppStatusResult-End-->

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## appInfo

```TypeScript
appInfo: AppInfo
```

Application information.

**Type:** [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ControlAppStatusResult-appInfo: AppInfo--><!--Device-ControlAppStatusResult-appInfo: AppInfo-End-->

**System capability:** SystemCapability.Security.Asset

## status

```TypeScript
status: ControlAppStatus
```

Control permission status.

**Type:** [ControlAppStatus](arkts-ability-abilitytoolaccessctrl-controlappstatus-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ControlAppStatusResult-status: ControlAppStatus--><!--Device-ControlAppStatusResult-status: ControlAppStatus-End-->

**System capability:** SystemCapability.Security.Asset
