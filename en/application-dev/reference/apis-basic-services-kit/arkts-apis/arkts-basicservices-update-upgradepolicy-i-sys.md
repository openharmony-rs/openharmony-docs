# UpgradePolicy (System API)

Sets the upgrade policy to control the upgrade behavior.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## autoUpgradePeriods

```TypeScript
autoUpgradePeriods: Array<UpgradePeriod>
```

Automatic update period.

This parameter is optional and is used when the automatic upgrade needs to be performed in a specified period (for example, at night). If this parameter is not passed, the value is an empty array **[]** by default, indicating that the automatic upgrade period is not limited and the upgrade can be performed at any time.

**Type:** Array&lt;[UpgradePeriod](arkts-basicservices-update-upgradeperiod-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## autoUpgradeStrategy

```TypeScript
autoUpgradeStrategy: boolean
```

Automatic upgrade policy.

The value **true** indicates that automatic upgrade is enabled, which is applicable to scenarios where the system needs to automatically complete the upgrade process to improve user experience. The value **false** indicates that automatic upgrade is disabled, which is applicable to scenarios where users need to manually confirm the upgrade to prevent unexpected upgrade or ensure that users are informed. Select a value based on user experience requirements and the upgrade control policy.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## downloadStrategy

```TypeScript
downloadStrategy: boolean
```

Automatic download policy.

The value **true** indicates that automatic download is enabled, which is applicable to scenarios where the system is expected to automatically detect and download the new version to reduce manual operations. The value **false** indicates that automatic download is disabled, which is applicable to scenarios where users need to manually confirm the download, preventing using the mobile data or storage space in the background. Select a value based on user preferences and mobile data policies.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
