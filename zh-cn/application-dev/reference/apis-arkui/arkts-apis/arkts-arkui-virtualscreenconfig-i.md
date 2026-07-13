# VirtualScreenConfig

创建虚拟屏幕的参数。

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

## density

```TypeScript
density: number
```

指定虚拟屏幕的密度，单位为px，该参数为浮点数。

**类型：** number

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

## height

```TypeScript
height: number
```

指定虚拟屏幕的高度，单位为px，该参数应为正整数。

**类型：** number

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

## name

```TypeScript
name: string
```

指定虚拟屏幕的名称，用户可自行定义。

**类型：** string

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

## supportsFocus

```TypeScript
supportsFocus?: boolean
```

指定虚拟屏幕是否可获得焦点。true表示可获焦，false表示不可获焦，默认值为true。

**类型：** boolean

**起始版本：** 22

**系统能力：** SystemCapability.Window.SessionManager

## surfaceId

```TypeScript
surfaceId: string
```

指定虚拟屏幕的surfaceId，用户可自行定义，该参数最大长度为4096个字节，超出最大长度时则取前4096个字节。

**类型：** string

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

## width

```TypeScript
width: number
```

指定虚拟屏幕的宽度，单位为px，该参数应为正整数。

**类型：** number

**起始版本：** 16

**系统能力：** SystemCapability.Window.SessionManager

