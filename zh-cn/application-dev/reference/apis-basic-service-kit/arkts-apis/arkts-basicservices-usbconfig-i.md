# USBConfig

USB配置，一个[USBDevice](arkts-basicservices-usbdevice-i.md)中可以含有多个配置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [USBConfiguration](arkts-basicservices-usbconfiguration-i.md)

**系统能力：** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: number
```

配置的属性。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [attributes](arkts-basicservices-usbconfiguration-i.md#attributes)

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: number
```

配置的唯一标识。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [id](arkts-basicservices-usbconfiguration-i.md#id)

**系统能力：** SystemCapability.USB.USBManager

## interfaces

```TypeScript
interfaces: Array<USBInterface>
```

配置支持的接口属性。

**类型：** Array<USBInterface>

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [interfaces](arkts-basicservices-usbconfiguration-i.md#interfaces)

**系统能力：** SystemCapability.USB.USBManager

## isRemoteWakeup

```TypeScript
isRemoteWakeup: boolean
```

检查当前配置是否支持远程唤醒。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isRemoteWakeup](arkts-basicservices-usbconfiguration-i.md#isremotewakeup)

**系统能力：** SystemCapability.USB.USBManager

## isSelfPowered

```TypeScript
isSelfPowered: boolean
```

检查当前配置是否支持独立电源。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSelfPowered](arkts-basicservices-usbconfiguration-i.md#isselfpowered)

**系统能力：** SystemCapability.USB.USBManager

## maxPower

```TypeScript
maxPower: number
```

最大功耗，以毫安为单位。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [maxPower](arkts-basicservices-usbconfiguration-i.md#maxpower)

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

配置的名称，可以为空。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [name](arkts-basicservices-usbconfiguration-i.md#name)

**系统能力：** SystemCapability.USB.USBManager

