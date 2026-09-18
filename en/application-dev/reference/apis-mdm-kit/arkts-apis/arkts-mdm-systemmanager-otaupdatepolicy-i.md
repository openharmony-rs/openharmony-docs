# OtaUpdatePolicy

Represents an OTA update policy.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## delayUpdateTime

```TypeScript
delayUpdateTime?: number
```

Period for which the update is postponed, in hours.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## disableSystemOtaUpdate

```TypeScript
disableSystemOtaUpdate?: boolean
```

Whether to disable public network upgrade. The value **true** indicates that public network upgrade is disabled, and the value **false** indicates the opposite. If this field is used as an input parameter of [systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md), the default value can be retained. The current configuration can be obtained via the [systemManager.getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md) API. After public network upgrade is disabled, you can perform intranet upgrade.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## installEndTime

```TypeScript
installEndTime?: number
```

End time (timestamp) of the installation window.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## installStartTime

```TypeScript
installStartTime?: number
```

Start time (timestamp) of the installation window.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## latestUpdateTime

```TypeScript
latestUpdateTime?: number
```

Latest update time (timestamp).

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## policyType

```TypeScript
policyType: PolicyType
```

Type of the update policy.

**Type:** [PolicyType](arkts-mdm-systemmanager-policytype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

Version of the software to update.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
