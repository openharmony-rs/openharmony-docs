# isSelfSuperAdmin

## Modules to Import

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## isSelfSuperAdmin

```TypeScript
function isSelfSuperAdmin(): boolean
```

Check if self is a super administrator.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-adminManager-function isSelfSuperAdmin(): boolean--><!--Device-adminManager-function isSelfSuperAdmin(): boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if self is a super device administrator, false if self is a normal device administrator or not an administrator. |
