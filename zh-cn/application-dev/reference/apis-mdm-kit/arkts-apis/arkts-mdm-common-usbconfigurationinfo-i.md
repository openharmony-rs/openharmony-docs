# USBConfigurationInfo

```TypeScript
export interface USBConfigurationInfo
```

USB配置信息。

**起始版本：** 26.1.0

<!--Device-common-export interface USBConfigurationInfo--><!--Device-common-export interface USBConfigurationInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { common } from '@kit.MDMKit';
```

## id

```TypeScript
id: number
```

配置ID。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-USBConfigurationInfo-id: number--><!--Device-USBConfigurationInfo-id: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## interfaces

```TypeScript
interfaces: Array<USBInterfaceInfo>
```

USB接口信息列表。

**类型：** Array&lt;[USBInterfaceInfo](arkts-mdm-common-usbinterfaceinfo-i.md)&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-USBConfigurationInfo-interfaces: Array<USBInterfaceInfo>--><!--Device-USBConfigurationInfo-interfaces: Array<USBInterfaceInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## isMount

```TypeScript
isMount: boolean
```

配置状态。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-USBConfigurationInfo-isMount: boolean--><!--Device-USBConfigurationInfo-isMount: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

配置名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-USBConfigurationInfo-name: string--><!--Device-USBConfigurationInfo-name: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
