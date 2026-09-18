# WindowStateInfo

Defines the application window state information.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## isOnDock

```TypeScript
isOnDock: boolean
```

Whether the application window is displayed on the bottom dock. For application on the bottom dock on tablets in PC mode and PCs/2-in-1 devices. For other devices, **false** is returned.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Application window name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: WindowState
```

Application window state.

**Type:** [WindowState](arkts-mdm-applicationmanager-windowstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## windowId

```TypeScript
windowId: number
```

Application window ID.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
