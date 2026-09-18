# TaskBody (System API)

Represents task data.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## errorMessages

```TypeScript
errorMessages: Array<ErrorMessage>
```

Error message.

**Type:** Array&lt;[ErrorMessage](arkts-basicservices-update-errormessage-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## installMode

```TypeScript
installMode: number
```

Install mode. The value range is [0, 2]. The value **0** indicates the regular upgrade, which is applicable to scenarios where users proactively trigger the upgrade. **1** indicates the upgrade at night, which is applicable to scenarios where automatic upgrade is performed at night. **2** indicates the automatic upgrade, which is applicable to scenarios where the system automatically detects and performs the upgrade. Select a value based on the upgrade policy and user experience requirements. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## progress

```TypeScript
progress: number
```

Progress, in percentage. The value range is [0, 100]. If the value is out of the range, an exception is thrown.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## status

```TypeScript
status: UpgradeStatus
```

Upgrade status, which indicates the current execution phase of the upgrade task. The value can be a download status (from **WAITING_DOWNLOAD** to **DOWNLOAD_FAIL**), installation status (from **WAITING_INSTALL** to **UPDATING**), effective status (from **WAITING_APPLY** to **APPLYING**), or the final result (**UPGRADE_SUCCESS** or **UPGRADE_FAIL**). This parameter is used for status monitoring, progress display, and exception handling.

**Type:** [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## subStatus

```TypeScript
subStatus: number
```

Sub-status. For details about the value range, see [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## versionComponents

```TypeScript
versionComponents: Array<VersionComponent>
```

Version components.

**Type:** Array&lt;[VersionComponent](arkts-basicservices-update-versioncomponent-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## versionDigestInfo

```TypeScript
versionDigestInfo: VersionDigestInfo
```

Version digest information.

**Type:** [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
