# USBInterface

一个[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md#USBConfiguration)中可以含有多个USBInterface，每个USBInterface提供一个功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-interface USBInterface--><!--Device-usbManager-interface USBInterface-End-->

**系统能力：** SystemCapability.USB.USBManager

## alternateSetting

```TypeScript
alternateSetting: int
```

在同一个接口中的多个描述符中进行切换设置。值的大小表示支持可选模式个数，其中0表示不支持可选模式。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-alternateSetting: int--><!--Device-USBInterface-alternateSetting: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## clazz

```TypeScript
clazz: int
```

设备类型。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-clazz: int--><!--Device-USBInterface-clazz: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpoints

```TypeScript
endpoints: Array<USBEndpoint>
```

当前接口所包含的端点。

**类型：** Array&lt;USBEndpoint&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-endpoints: Array<USBEndpoint>--><!--Device-USBInterface-endpoints: Array<USBEndpoint>-End-->

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: int
```

接口的唯一标识。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-id: int--><!--Device-USBInterface-id: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

接口名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-name: string--><!--Device-USBInterface-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

## protocol

```TypeScript
protocol: int
```

接口的协议。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-protocol: int--><!--Device-USBInterface-protocol: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## subClass

```TypeScript
subClass: int
```

设备子类。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBInterface-subClass: int--><!--Device-USBInterface-subClass: int-End-->

**系统能力：** SystemCapability.USB.USBManager

