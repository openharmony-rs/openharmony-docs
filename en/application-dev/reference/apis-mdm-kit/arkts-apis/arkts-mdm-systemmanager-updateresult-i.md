# UpdateResult

```TypeScript
interface UpdateResult
```

Represents the update result information.

**Since:** 12

<!--Device-systemManager-interface UpdateResult--><!--Device-systemManager-interface UpdateResult-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## errorInfo

```TypeScript
errorInfo: ErrorInfo
```

Error information.

**Type:** [ErrorInfo](arkts-mdm-systemmanager-errorinfo-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdateResult-errorInfo: ErrorInfo--><!--Device-UpdateResult-errorInfo: ErrorInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## status

```TypeScript
status: UpdateStatus
```

System update status.

**Type:** [UpdateStatus](arkts-mdm-systemmanager-updatestatus-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdateResult-status: UpdateStatus--><!--Device-UpdateResult-status: UpdateStatus-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

Current version of the system.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdateResult-version: string--><!--Device-UpdateResult-version: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
