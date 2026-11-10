# MainWindowStates

```TypeScript
interface MainWindowStates
```

Main window states information.

**Since:** 26.1.0

<!--Device-applicationManager-interface MainWindowStates--><!--Device-applicationManager-interface MainWindowStates-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MainWindowStates-bundleName: string--><!--Device-MainWindowStates-bundleName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## pid

```TypeScript
pid: number
```

Process ID of the application.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MainWindowStates-pid: number--><!--Device-MainWindowStates-pid: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: WindowState
```

State of the main window.

**Type:** [WindowState](arkts-mdm-applicationmanager-windowstate-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MainWindowStates-state: WindowState--><!--Device-MainWindowStates-state: WindowState-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
