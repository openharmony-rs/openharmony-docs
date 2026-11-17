# USBConfigurationInfo

```TypeScript
export interface USBConfigurationInfo
```

Indicates the USB configuration information.

**Since:** 26.1.0

<!--Device-common-export interface USBConfigurationInfo--><!--Device-common-export interface USBConfigurationInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { common } from '@kit.MDMKit';
```

## id

```TypeScript
id: number
```

Configuration ID.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-USBConfigurationInfo-id: number--><!--Device-USBConfigurationInfo-id: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## interfaces

```TypeScript
interfaces: Array<USBInterfaceInfo>
```

USB interface information list.

**Type:** Array&lt;[USBInterfaceInfo](arkts-mdm-common-usbinterfaceinfo-i.md)&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-USBConfigurationInfo-interfaces: Array<USBInterfaceInfo>--><!--Device-USBConfigurationInfo-interfaces: Array<USBInterfaceInfo>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## isMount

```TypeScript
isMount: boolean
```

Configuration state.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-USBConfigurationInfo-isMount: boolean--><!--Device-USBConfigurationInfo-isMount: boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Configuration name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-USBConfigurationInfo-name: string--><!--Device-USBConfigurationInfo-name: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
