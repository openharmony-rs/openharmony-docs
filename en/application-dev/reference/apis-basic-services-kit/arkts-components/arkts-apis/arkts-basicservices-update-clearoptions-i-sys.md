# ClearOptions (System API)

Defines the clearing options, which specify the errors to be cleared.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## status

```TypeScript
status: UpgradeStatus
```

Exception status, which is used to specify the status to be cleared. This parameter can be set to **UPGRADE_FAIL** only when the **upgrade** method fails to be executed and its status is **UPGRADE_FAIL**.

Use scenarios: If the upgrade fails (with the status of **UPGRADE_FAIL**), the system retains the error state to prevent the upgrade from being performed again. In this case, you need to call **status** passed by **clearError** so that errors can be cleared, and the system can be restored to the initial state to restart the upgrade process.

A common value is **UPGRADE_FAIL**, including upgrade failure. Note: Only the **UPGRADE_FAIL** status can be cleared.

**Type:** [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
