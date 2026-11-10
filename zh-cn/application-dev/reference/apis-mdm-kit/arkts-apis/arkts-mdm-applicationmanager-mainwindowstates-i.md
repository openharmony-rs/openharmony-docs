# MainWindowStates

```TypeScript
interface MainWindowStates
```

主窗口显示信息。

**起始版本：** 26.1.0

<!--Device-applicationManager-interface MainWindowStates--><!--Device-applicationManager-interface MainWindowStates-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MainWindowStates-bundleName: string--><!--Device-MainWindowStates-bundleName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## pid

```TypeScript
pid: number
```

应用进程ID。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MainWindowStates-pid: number--><!--Device-MainWindowStates-pid: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: WindowState
```

主窗口状态。

**类型：** [WindowState](arkts-mdm-applicationmanager-windowstate-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MainWindowStates-state: WindowState--><!--Device-MainWindowStates-state: WindowState-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
