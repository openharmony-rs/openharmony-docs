# UpgradeAction (System API)

```TypeScript
export enum UpgradeAction
```

Represents an update mode.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## UPGRADE

```TypeScript
UPGRADE = 'upgrade'
```

Difference package, which contains only the different parts between the current version and the target version. It is applicable to the incremental upgrade when the basic version has been installed. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## RECOVERY

```TypeScript
RECOVERY = 'recovery'
```

Repair package, which is a special upgrade package used to fix system errors or restore system functions. It is applicable to repair in case of system failure. For details, see [Upgrading Service Terms] (../../../basic-services/update/update-kit-term.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
