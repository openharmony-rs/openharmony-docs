# WindowStateInfo

```TypeScript
interface WindowStateInfo
```

Defines the application window state information.

**Since:** 26.0.0

<!--Device-applicationManager-interface WindowStateInfo--><!--Device-applicationManager-interface WindowStateInfo-End-->

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

<!--Device-WindowStateInfo-isOnDock: boolean--><!--Device-WindowStateInfo-isOnDock: boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Application window name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStateInfo-name: string--><!--Device-WindowStateInfo-name: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: WindowState
```

Application window state.

**Type:** [WindowState](arkts-mdm-applicationmanager-windowstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStateInfo-state: WindowState--><!--Device-WindowStateInfo-state: WindowState-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## windowId

```TypeScript
windowId: number
```

Application window ID.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStateInfo-windowId: number--><!--Device-WindowStateInfo-windowId: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
