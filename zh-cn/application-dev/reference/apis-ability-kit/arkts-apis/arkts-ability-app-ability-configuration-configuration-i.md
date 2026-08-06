# Configuration

定义了应用运行时的环境变量，包含语言、深浅色、屏幕方向、字体等。开发者可以通过订阅环境变量，适配不同用户偏好，提升交互体验。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface Configuration--><!--Device-unnamed-export interface Configuration-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

表示应用深浅色模式，默认为浅色。 支持开发者\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 取值范围： - COLOR\_MODE\_NOT\_SET：未设置 - COLOR\_MODE\_LIGHT：浅色模式 - COLOR\_MODE\_DARK：深色模式

**类型：** ConfigurationConstant.ColorMode

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-colorMode?: ConfigurationConstant.ColorMode--><!--Device-Configuration-colorMode?: ConfigurationConstant.ColorMode-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## direction

```TypeScript
direction?: ConfigurationConstant.Direction
```

表示应用屏幕方向。 取值范围： - DIRECTION\_NOT\_SET：未设置 - DIRECTION\_HORIZONTAL：水平方向 - DIRECTION\_VERTICAL：垂直方向 该环境变量支持在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件和 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_组件中订阅，不支持在 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_组件容器中订阅。

**类型：** ConfigurationConstant.Direction

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-direction?: ConfigurationConstant.Direction--><!--Device-Configuration-direction?: ConfigurationConstant.Direction-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## displayId

```TypeScript
displayId?: long
```

表示应用所在的物理屏幕ID。 该环境变量支持在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件和 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_组件中订阅，不支持在 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_组件容器中订阅。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-displayId?: long--><!--Device-Configuration-displayId?: long-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontId

```TypeScript
fontId?: string
```

表示应用字体的唯一ID。

**类型：** string

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontId?: string--><!--Device-Configuration-fontId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontSizeScale

```TypeScript
fontSizeScale?: double
```

表示字体大小缩放比例，取值为非负数，默认值为1。 支持开发者\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** double

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontSizeScale?: double--><!--Device-Configuration-fontSizeScale?: double-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fontWeightScale

```TypeScript
fontWeightScale?: double
```

表示字体粗细缩放比例，取值为非负数，默认值为1。

**类型：** double

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-fontWeightScale?: double--><!--Device-Configuration-fontWeightScale?: double-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## hasPointerDevice

```TypeScript
hasPointerDevice?: boolean
```

表示指针设备是否已连接，如键鼠、触控板等。true表示设备已连接，false表示设备未连接。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-hasPointerDevice?: boolean--><!--Device-Configuration-hasPointerDevice?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## language

```TypeScript
language?: string
```

表示应用当前语言，例如“zh"(中文)，“en”（英文）。 支持开发者\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 取值范围参考\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-language?: string--><!--Device-Configuration-language?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## locale

```TypeScript
locale?: Intl.Locale
```

表示区域设置。 应用会根据当前的区域设置自动调整其行为，以符合用户的本地化需求。该属性可以通过设置系统语言、设置系统地区和设置应用偏好语言等方式设置。

**类型：** Intl.Locale

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-locale?: Intl.Locale--><!--Device-Configuration-locale?: Intl.Locale-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## mcc

```TypeScript
mcc?: string
```

表示移动设备国家代码。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-mcc?: string--><!--Device-Configuration-mcc?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## mnc

```TypeScript
mnc?: string
```

表示移动设备网络代码。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-mnc?: string--><!--Device-Configuration-mnc?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## screenDensity

```TypeScript
screenDensity?: ConfigurationConstant.ScreenDensity
```

表示屏幕显示密度。 取值范围： - SCREEN\_DENSITY\_NOT\_SET：未设置 - SCREEN\_DENSITY\_SDPI：120 - SCREEN\_DENSITY\_MDPI：160 - SCREEN\_DENSITY\_LDPI：240 - SCREEN\_DENSITY\_XLDPI：320 - SCREEN\_DENSITY\_XXLDPI：480 - SCREEN\_DENSITY\_XXXLDPI：640 字体显示大小与屏幕像素密度呈正相关关系。通过监听屏幕像素密度变化，可以感知字体显示大小的调整。通常情况下，对于相同的物理尺寸，屏幕像素密度越高，字体显示效果越大。 该环境变量支持在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_组件和 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_组件中订阅，不支持在 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_组件容器中订阅。

**类型：** ConfigurationConstant.ScreenDensity

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Configuration-screenDensity?: ConfigurationConstant.ScreenDensity--><!--Device-Configuration-screenDensity?: ConfigurationConstant.ScreenDensity-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

