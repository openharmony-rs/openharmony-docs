# USBDeviceInfo（系统接口）

USB设备详细信息，继承自[DeviceInfo](arkts-driverdevelopment-deviceinfo-i-sys.md)。

**继承/实现关系：** USBDeviceInfo extends [DeviceInfo](arkts-driverdevelopment-deviceinfo-i-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## interfaceDescList

```TypeScript
interfaceDescList: Array<Readonly<USBInterfaceDesc>>
```

USB设备接口描述符列表。

**类型：** Array<Readonly<USBInterfaceDesc>>

**起始版本：** 12

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: number
```

USB设备Product ID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

## vendorId

```TypeScript
vendorId: number
```

USB设备Vendor ID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Driver.ExternalDevice

**系统接口：** 此接口为系统接口。

