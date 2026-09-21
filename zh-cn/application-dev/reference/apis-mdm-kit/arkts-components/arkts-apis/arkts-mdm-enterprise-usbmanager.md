# @ohos.enterprise.usbManager(USB管理)

本模块提供USB管理能力。

> **说明：** 
> 
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。
> 
> 全局通用限制类策略由restrictions统一提供，若要全局禁用USB，请参考
> [@ohos.enterprise.restrictions（限制类策略）](arkts-mdm-enterprise-restrictions.md)。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md) | 添加USB设备可用名单。 |
| [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md) | 添加禁止使用的USB设备类型。与[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md)接口不同的是，本接口可以不按照[defined-class-codes](https://www.usb.org/defined-class-codes)标准进行匹配。对已连接的USB设备热生效，无需重新插拔，例如USB线控耳机正常使用时，调用本接口禁用该耳机，会导致耳机不可用。 |
| [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md) | 添加禁止使用的USB设备类型。 |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices) | 获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。 |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices-1) | 获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。 |
| [getDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-getdisallowedpermissiveusbdevices-f.md) | 获取通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口禁用的USB设备类型。 |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices) | 获取禁止使用的USB设备类型。 |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices-1) | 获取禁止使用的USB设备类型。 |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy) | 获取USB存储设备（baseClass = 0x08）访问策略。 |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy-1) | 获取USB存储设备（baseClass = 0x08）访问策略。 |
| [removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md) | 移除USB设备可用名单。 |
| [removeDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-removedisallowedpermissiveusbdevices-f.md) | 移除通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口禁用的USB设备类型。被移除的USB设备类型可恢复正常使用。 |
| [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md) | 移除禁止使用的USB设备类型。 |
| [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md) | 设置USB存储设备（baseClass = 0x08）访问策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableUsb](arkts-mdm-usbmanager-disableusb-f-sys.md) | 设置禁用或启用USB。 |
| [isUsbDisabled](arkts-mdm-usbmanager-isusbdisabled-f-sys.md) | 查询USB是否禁用。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy) | 设置USB的读写策略。使用callback异步回调。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy-1) | 设置USB的读写策略。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PermissiveUsbDeviceType](arkts-mdm-usbmanager-permissiveusbdevicetype-i.md) | USB设备类型信息，支持部分字段匹配。 |
| [UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md) | USB设备ID信息。 |
| [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md) | USB设备类型信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Descriptor](arkts-mdm-usbmanager-descriptor-e.md) | USB描述符的枚举。 |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | USB存储设备访问策略的枚举。 |
