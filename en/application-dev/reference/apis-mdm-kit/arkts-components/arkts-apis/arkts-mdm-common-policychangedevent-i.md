# PolicyChangedEvent

Defines the policy change event.

This API is used as a callback input parameter of [onAdminPolicyChanged](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onadminpolicychanged).

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { common } from '@kit.MDMKit';
```

## bundleName

```TypeScript
bundleName: string
```

App bundle name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## functionName

```TypeScript
functionName: string
```

API name. For example, if the [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md) API is called, the value of this parameter is **setPasswordPolicy**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## parameters

```TypeScript
parameters: string
```

Input parameter value (excluding the **admin** parameter) when an API is called. The value is a JSON string. For example, if the [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md) API is called, the return value of this parameter is **{"policy":{"complexityRegex":"^(?=.*[a-zA-Z])(?=.*\\d).{8},&#36;","validityPeriod":1808309786000,"additionalDescription":"It must contain at least eight characters, including digits and letters."}}**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## time

```TypeScript
time: number
```

Timestamp when an API is called, in milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
