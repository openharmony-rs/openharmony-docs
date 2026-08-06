# VirtualScreenConfig

创建虚拟屏幕的参数。

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-display-interface VirtualScreenConfig--><!--Device-display-interface VirtualScreenConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

## density

```TypeScript
density: double
```

指定虚拟屏幕的密度，单位为px，该参数为浮点数。

**类型：** double

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-density: double--><!--Device-VirtualScreenConfig-density: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

## height

```TypeScript
height: long
```

指定虚拟屏幕的高度，单位为px，该参数应为正整数。

**类型：** long

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-height: long--><!--Device-VirtualScreenConfig-height: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## name

```TypeScript
name: string
```

指定虚拟屏幕的名称，用户可自行定义。

**类型：** string

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-name: string--><!--Device-VirtualScreenConfig-name: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## supportsFocus

```TypeScript
supportsFocus?: boolean
```

指定虚拟屏幕是否可获得焦点。true表示可获焦，false表示不可获焦，默认值为true。

**类型：** boolean

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-supportsFocus?: boolean--><!--Device-VirtualScreenConfig-supportsFocus?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## surfaceId

```TypeScript
surfaceId: string
```

指定虚拟屏幕的surfaceId，用户可自行定义，该参数最大长度为4096个字节，超出最大长度时则取前4096个字节。

**类型：** string

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-surfaceId: string--><!--Device-VirtualScreenConfig-surfaceId: string-End-->

**系统能力：** SystemCapability.Window.SessionManager

## width

```TypeScript
width: long
```

指定虚拟屏幕的宽度，单位为px，该参数应为正整数。

**类型：** long

**起始版本：** 16

**ArkTS模式：** ArkTS-Dyn起始版本为16；ArkTS-Sta起始版本为23。

<!--Device-VirtualScreenConfig-width: long--><!--Device-VirtualScreenConfig-width: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

