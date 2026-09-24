# isFeatureSupported

## Modules to Import

```TypeScript
import { common } from '@kit.MDMKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(feature: ManagedFeature): boolean
```

Checks whether a specified feature is supported.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| feature | [ManagedFeature](arkts-mdm-common-managedfeature-e.md) | Yes | The feature of enterprise device management. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the specified feature is supported, and the value **false** indicates the opposite. |
