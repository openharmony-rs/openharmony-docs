# SystemBarRegionTint（系统接口）

单个导航栏或状态栏回调信息。

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## backgroundColor

```TypeScript
backgroundColor?: string
```

系统栏背景颜色，为十六进制RGB或ARGB颜色，不区分大小写，例如'#00FF00'或'#FF00FF00'。 默认值为'0x66000000'。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## contentColor

```TypeScript
contentColor?: string
```

系统栏文字颜色。 默认值为'0xE5FFFFFF'。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## isEnable

```TypeScript
isEnable?: boolean
```

当前系统栏是否显示。true表示显示；false表示不显示。默认值为true。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## region

```TypeScript
region?: Rect
```

当前系统栏的位置及大小。默认值为{0,0,0,0}。

**类型：** Rect

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: WindowType
```

当前属性改变的系统栏类型，仅支持类型为导航栏、状态栏的系统栏。

**类型：** WindowType

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

