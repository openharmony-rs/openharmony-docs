# WindowStateInfo

应用窗口状态信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## isOnDock

```TypeScript
isOnDock: boolean
```

表示应用窗口是否在底部Dock栏上显示。PC/2in1设备和Tablet设备的PC模式的应用在底部Dock栏上返回true，其他设备返回false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

应用窗口名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## state

```TypeScript
state: WindowState
```

应用窗口状态。

**类型：** [WindowState](arkts-mdm-applicationmanager-windowstate-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## windowId

```TypeScript
windowId: number
```

应用窗口ID。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
