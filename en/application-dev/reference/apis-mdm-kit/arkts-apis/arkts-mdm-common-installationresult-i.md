# InstallationResult

An object that holds the application installation result.

This object is used as a callback parameter in [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onmarketappinstallresult).

**Since:** 22

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { common } from '@kit.MDMKit';
```

## message

```TypeScript
message: string
```

Application installation result message.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## result

```TypeScript
result: Result
```

Application installation result. **SUCCESS** indicates that the application is successfully installed and can be properly used. **FAIL** indicates that the application fails to be installed and is unavailable.

**Type:** [Result](arkts-mdm-common-result-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
