# @ohos.enterprise.usbManager(USB管理)

本模块提供USB管理能力。

> **说明：** 
> 
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。
> 
> 全局通用限制类策略由restrictions统一提供，若要全局禁用USB，请参考
> [@ohos.enterprise.restrictions（限制类策略）](arkts-mdm-enterprise-restrictions.md)。

**起始版本：** 12

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
| [addAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-addallowedopticaldiscdriveburnusbdevices-f.md#addallowedopticaldiscdriveburnusbdevices) | 增加支持CD/DVD刻录的USB设备列表。 |
| [addAllowedUsbDevices](arkts-mdm-usbmanager-addallowedusbdevices-f.md#addallowedusbdevices) | 添加USB设备可用名单。 |
| [addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md#adddisallowedpermissiveusbdevices) | 添加禁止使用的USB设备类型。与[addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md)接口不同的是，本接口可以不按照[defined-class-codes](https://www.usb.org/defined-class-codes)标准进行匹配。对已连接的USB设备热生效，无需重新插拔，例如USB线控耳机正常使用时，调用本接口禁用该耳机，会导致耳机不可用。 |
| [addDisallowedUsbDevices](arkts-mdm-usbmanager-adddisallowedusbdevices-f.md#adddisallowedusbdevices) | 添加禁止使用的USB设备类型。 |
| [getAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-getallowedopticaldiscdriveburnusbdevices-f.md#getallowedopticaldiscdriveburnusbdevices) | 获取支持CD/DVD刻录的USB设备列表。 |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices) | 获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。 |
| [getAllowedUsbDevices](arkts-mdm-usbmanager-getallowedusbdevices-f.md#getallowedusbdevices) | 获取USB设备可用名单。一般使用场景：在修改策略前，需要先获取现有策略进行评估；管理界面需要展示当前的USB存储设备访问控制状态。 |
| [getDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-getdisallowedpermissiveusbdevices-f.md#getdisallowedpermissiveusbdevices) | 获取通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口禁用的USB设备类型。 |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices) | 获取禁止使用的USB设备类型。 |
| [getDisallowedUsbDevices](arkts-mdm-usbmanager-getdisallowedusbdevices-f.md#getdisallowedusbdevices) | 获取禁止使用的USB设备类型。 |
| [getExternalStorageDeviceInfos](arkts-mdm-usbmanager-getexternalstoragedeviceinfos-f.md#getexternalstoragedeviceinfos) | 获取当前设备的卷信息。 |
| [getUsbSerialNumber](arkts-mdm-usbmanager-getusbserialnumber-f.md#getusbserialnumber) | 获取USB设备的序列号。 |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy) | 获取USB存储设备（baseClass = 0x08）访问策略。 |
| [getUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-getusbstoragedeviceaccesspolicy-f.md#getusbstoragedeviceaccesspolicy) | 获取USB存储设备（baseClass = 0x08）访问策略。 |
| [isExternalStorageInterceptEnable](arkts-mdm-usbmanager-isexternalstorageinterceptenable-f.md#isexternalstorageinterceptenable) | 查询外置存储挂载使能状态。 |
| [removeAllowedOpticalDiscDriveBurnUsbDevices](arkts-mdm-usbmanager-removeallowedopticaldiscdriveburnusbdevices-f.md#removeallowedopticaldiscdriveburnusbdevices) | 将USB设备从支持CD/DVD刻录的USB设备列表中移除。 |
| [removeAllowedUsbDevices](arkts-mdm-usbmanager-removeallowedusbdevices-f.md#removeallowedusbdevices) | 移除USB设备可用名单。 |
| [removeDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-removedisallowedpermissiveusbdevices-f.md#removedisallowedpermissiveusbdevices) | 移除通过[addDisallowedPermissiveUsbDevices](arkts-mdm-usbmanager-adddisallowedpermissiveusbdevices-f.md)接口禁用的USB设备类型。被移除的USB设备类型可恢复正常使用。 |
| [removeDisallowedUsbDevices](arkts-mdm-usbmanager-removedisallowedusbdevices-f.md#removedisallowedusbdevices) | 移除禁止使用的USB设备类型。 |
| [setExternalStorageDeviceMountPolicy](arkts-mdm-usbmanager-setexternalstoragedevicemountpolicy-f.md#setexternalstoragedevicemountpolicy) | 设置外部存储设备的挂载策略。 |
| [setExternalStorageInterceptEnable](arkts-mdm-usbmanager-setexternalstorageinterceptenable-f.md#setexternalstorageinterceptenable) | 设置外置存储挂载使能状态。 |
| [setUsbStorageDeviceAccessPolicy](arkts-mdm-usbmanager-setusbstoragedeviceaccesspolicy-f.md#setusbstoragedeviceaccesspolicy) | 设置USB存储设备（baseClass = 0x08）访问策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableUsb](arkts-mdm-usbmanager-disableusb-f-sys.md#disableusb) | 设置禁用或启用USB。 |
| [isUsbDisabled](arkts-mdm-usbmanager-isusbdisabled-f-sys.md#isusbdisabled) | 查询USB是否禁用。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy) | 设置USB的读写策略。使用callback异步回调。 |
| [setUsbPolicy](arkts-mdm-usbmanager-setusbpolicy-f-sys.md#setusbpolicy) | 设置USB的读写策略。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [PermissiveUsbDeviceType](arkts-mdm-usbmanager-permissiveusbdevicetype-i.md) | USB设备类型信息，支持部分字段匹配。 |
| [UsbDevice](arkts-mdm-usbmanager-usbdevice-i.md) | 表示USB设备标识信息。 |
| [UsbDeviceId](arkts-mdm-usbmanager-usbdeviceid-i.md) | USB设备ID信息。 |
| [UsbDeviceType](arkts-mdm-usbmanager-usbdevicetype-i.md) | USB设备类型信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Descriptor](arkts-mdm-usbmanager-descriptor-e.md) | USB描述符的枚举。 |
| [MountPolicy](arkts-mdm-usbmanager-mountpolicy-e.md) | 挂载策略。 |
| [UsbPolicy](arkts-mdm-usbmanager-usbpolicy-e.md) | USB存储设备访问策略的枚举。 |
