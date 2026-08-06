# AVCastPicker

本模块提供创建投播组件AVCastPicker的功能，提供设备发现连接的统一入口。 > **说明：** > > - 示例效果请以真机为准，当前DevEco Studio预览器无实际投播功能。\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_ > > - 当前组件的使用，依赖于设备支持“设备选择界面”。当前暂无OpenHarmony设备支持，需要OEM厂商实现具体的“设备选择界面”。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Component

<!--Device-unnamed-declare struct AVCastPicker--><!--Device-unnamed-declare struct AVCastPicker-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## build

```TypeScript
build(): void
```

构造组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

<!--Device-AVCastPicker-build(): void--><!--Device-AVCastPicker-build(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## activeColor

```TypeScript
activeColor?: Color | int | string
```

设备连接成功状态下投播组件的颜色。 未设置时，系统将优先根据normalColor的颜色匹配；如果normalColor也未设置，将采用colorMode下的颜色设置。

**类型：** Color \| int \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-activeColor?: Color | int | string--><!--Device-AVCastPicker-activeColor?: Color | int | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## colorMode

```TypeScript
colorMode?: AVCastPickerColorMode
```

显示模式。默认值为AUTO。 - 当colorMode设置为AUTO时，跟随系统的深浅色模式的默认色值。 - 当colorMode设置为DARK、LIGHT时，使用对应模式的系统预设色值。

**类型：** AVCastPickerColorMode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-colorMode?: AVCastPickerColorMode--><!--Device-AVCastPicker-colorMode?: AVCastPickerColorMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## customPicker

```TypeScript
customPicker?: CustomBuilder
```

自定义样式。建议使用自定义组件样式，可有效提升组件显示速度。 If not set, system will show the default appearance for different device type.

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @BuilderParam

<!--Device-AVCastPicker-customPicker?: CustomBuilder--><!--Device-AVCastPicker-customPicker?: CustomBuilder-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## normalColor

```TypeScript
normalColor?: Color | int | string
```

正常状态下投播组件的颜色。 未设置时，将采用colorMode下的颜色设置。

**类型：** Color \| int \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-normalColor?: Color | int | string--><!--Device-AVCastPicker-normalColor?: Color | int | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## onStateChange

```TypeScript
onStateChange?: OnPickerStateCallback
```

投播状态更改回调。

**类型：** OnPickerStateCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-onStateChange?: OnPickerStateCallback--><!--Device-AVCastPicker-onStateChange?: OnPickerStateCallback-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## pickerStyle

```TypeScript
pickerStyle?: AVCastPickerStyle
```

投播样式。 - 当sessionType是audio或者video时，默认值为STYLE\_PANEL。 - 当sessionType是voice\_call或者video\_call时，默认值为STYLE\_MENU，且不可修改为STYLE\_PANEL。

**类型：** AVCastPickerStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-pickerStyle?: AVCastPickerStyle--><!--Device-AVCastPicker-pickerStyle?: AVCastPickerStyle-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## sessionType

```TypeScript
sessionType?: string
```

会话类型，可参考[AVSessionType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。默认值为当前应用创建的AVSessionType。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-sessionType?: string--><!--Device-AVCastPicker-sessionType?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

