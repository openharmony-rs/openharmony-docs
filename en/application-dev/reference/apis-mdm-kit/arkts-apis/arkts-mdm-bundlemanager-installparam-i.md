# InstallParam

Defines the parameters for application installation.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## installFlag

```TypeScript
installFlag?: number
```

Installation flag.

**0** (default value) indicates fresh installation of the application, **1** indicates overlay installation of the application, and **2** indicates installation-free.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## parameters

```TypeScript
parameters?: Record<string, string>
```

Extended parameters. The default value is null. The key can be **ohos.bms.param.enterpriseForAllUser**. If the corresponding value is set **true**, the application is installed for all users.

**Type:** Record&lt;string, string&gt;

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## userId

```TypeScript
userId?: number
```

User ID, which must be greater than or equal to 0. The default value is the user ID of the caller.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
