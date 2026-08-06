# USBConfiguration

USB配置，一个[USBDevice]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中可以含有多个配置。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-usbManager-interface USBConfiguration--><!--Device-usbManager-interface USBConfiguration-End-->

**系统能力：** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: int
```

配置的属性。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-attributes: int--><!--Device-USBConfiguration-attributes: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## id

```TypeScript
id: int
```

配置的唯一标识。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-id: int--><!--Device-USBConfiguration-id: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## interfaces

```TypeScript
interfaces: Array<USBInterface>
```

配置支持的接口属性。

**类型：** Array&lt;USBInterface&gt;

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-interfaces: Array<USBInterface>--><!--Device-USBConfiguration-interfaces: Array<USBInterface>-End-->

**系统能力：** SystemCapability.USB.USBManager

## isRemoteWakeup

```TypeScript
isRemoteWakeup: boolean
```

检查当前配置是否支持远程唤醒。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-isRemoteWakeup: boolean--><!--Device-USBConfiguration-isRemoteWakeup: boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

## isSelfPowered

```TypeScript
isSelfPowered: boolean
```

检查当前配置是否支持独立电源。true表示支持，false表示不支持。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-isSelfPowered: boolean--><!--Device-USBConfiguration-isSelfPowered: boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

## maxPower

```TypeScript
maxPower: int
```

最大功耗。（单位：毫安）。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-maxPower: int--><!--Device-USBConfiguration-maxPower: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## name

```TypeScript
name: string
```

配置的名称，可以为空。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-USBConfiguration-name: string--><!--Device-USBConfiguration-name: string-End-->

**系统能力：** SystemCapability.USB.USBManager

