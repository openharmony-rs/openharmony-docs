# USBDeviceInfo（系统接口）

USB设备详细信息，继承自[DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md#DeviceInfo（系统接口）)。

**继承/实现关系：** USBDeviceInfo extends [DeviceInfo](arkts-driverdevelopment-devicemanager-deviceinfo-i-sys.md#DeviceInfo（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-deviceManager-interface USBDeviceInfo--><!--Device-deviceManager-interface USBDeviceInfo-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## interfaceDescList

```TypeScript
interfaceDescList: Array<Readonly<USBInterfaceDesc>>
```

USB设备接口描述符列表。

**类型：** Array&lt;Readonly&lt;[USBInterfaceDesc](arkts-driverdevelopment-devicemanager-usbinterfacedesc-i-sys.md)&gt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBDeviceInfo-interfaceDescList: Array<Readonly<USBInterfaceDesc>>--><!--Device-USBDeviceInfo-interfaceDescList: Array<Readonly<USBInterfaceDesc>>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: int
```

USB设备Product ID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBDeviceInfo-productId: int--><!--Device-USBDeviceInfo-productId: int-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## vendorId

```TypeScript
vendorId: int
```

USB设备Vendor ID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBDeviceInfo-vendorId: int--><!--Device-USBDeviceInfo-vendorId: int-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

