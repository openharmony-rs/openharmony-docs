# @ohos.enterprise.usbManager

本模块提供USB管理能力。
> **说明**：  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。  
>  
> 全局通用限制类策略由restrictions统一提供，若要全局禁用USB，请参考  
> [@ohos.enterprise.restrictions（限制类策略）](arkts-enterprise-restrictions.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace usbManager--><!--Device-unnamed-declare namespace usbManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices) | 添加USB设备可用名单。  以下情况下，调用本接口会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备USB或者USB转串口能力。2. 已经通过[setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy)接口设置了USB存储设备访问策略为禁用。3. 已经通过[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices)接口添加了禁止使用的USB设备类型。 |
| [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices) | 添加禁止使用的USB设备类型。  以下情况下，调用本接口会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备USB能力。2. 已经通过[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices)接口添加了USB设备可用名单。3. 已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount)接口禁用了某用户USB存储设备写入能力。 |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices) | 获取USB设备可用名单。 |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices) | 获取禁止使用的USB设备类型。 |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy) | 获取USB存储设备访问策略。 |
| [removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeallowedusbdevices) | 移除USB设备可用名单。 |
| [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices) | 移除禁止使用的USB设备类型。 |
| [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy) | 设置USB存储设备访问策略。 > **说明**：  > > 在调用接口前，确保已暂停USB存储设备的读写操作，保证操作的稳定性和数据的完整性，否则可能出现不可预期的异常。  以下情况下，通过本接口设置USB存储设备访问策略为可读可写/只读，会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备USB能力。2. 已经通过[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices)接口将存储类型的USB设备添加为禁止使用的USB设备类型。3. 已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount)接口禁用了某用户USB存储设备写入能力。  以下情况下，通过本接口设置USB存储设备访问策略为禁用，会报策略冲突：  1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setdisallowedpolicy)接口禁用了设备USB能力。2. 已经通过[addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices)接口添加了USB设备可用名单。3. 已经通过[setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setdisallowedpolicyforaccount)接口禁用了某用户USB存储设备写入能力。  通过本接口设置，或者通过[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices)接口添加存储类型的USB设备，均可禁用USB存储设备。推荐使用后者。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableUsb](arkts-mdm-usbmanager-disableusb-f-sys.md#disableusb) | 设置禁用或启用USB。 |
| [isUsbDisabled](arkts-mdm-usbmanager-isusbdisabled-f-sys.md#isusbdisabled) | 查询USB是否禁用。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy) | 设置USB的读写策略。使用callback异步回调。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy-1) | 设置USB的读写策略。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md) | USB设备ID信息。 |
| [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md) | USB设备类型信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Descriptor](arkts-mdm-usbmanager-descriptor-e.md) | USB描述符的枚举。 |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | USB读写策略的枚举。 |

