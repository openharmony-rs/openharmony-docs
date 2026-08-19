# AVCastPicker

本模块提供创建投播组件AVCastPicker的功能，提供设备发现连接的统一入口。 > **说明：** > > - 示例效果请以真机为准，当前DevEco Studio预览器无实际投播功能。<!--Del--> > > - 当前组件的使用，依赖于设备支持“设备选择界面”。当前暂无OpenHarmony设备支持，需要OEM厂商实现具体的“设备选择界面”。<!--DelEnd-->

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare struct AVCastPicker--><!--Device-unnamed-declare struct AVCastPicker-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## 导入模块

```TypeScript
```

## build

```TypeScript
@Builder
  build(): void
```

构造组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@Builder  build(): void--><!--Device-AVCastPicker-@Builder  build(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## activeColor

```TypeScript
@PropRef
  activeColor?: Color | int | string
```

设备连接成功状态下投播组件的颜色。 未设置时，系统将优先根据normalColor的颜色匹配；如果normalColor也未设置，将采用colorMode下的颜色设置。

**类型：** [Color](arkts-na-enums-color-e.md) \| int \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@PropRef  activeColor?: Color | int | string--><!--Device-AVCastPicker-@PropRef  activeColor?: Color | int | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## colorMode

```TypeScript
@PropRef
  colorMode?: AVCastPickerColorMode
```

显示模式。默认值为AUTO。 - 当colorMode设置为AUTO时，跟随系统的深浅色模式的默认色值。 - 当colorMode设置为DARK、LIGHT时，使用对应模式的系统预设色值。

**类型：** [AVCastPickerColorMode](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpickerparam-avcastpickercolormode-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@PropRef  colorMode?: AVCastPickerColorMode--><!--Device-AVCastPicker-@PropRef  colorMode?: AVCastPickerColorMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## customPicker

```TypeScript
@BuilderParam
  customPicker?: CustomBuilder
```

自定义样式。建议使用自定义组件样式，可有效提升组件显示速度。 If not set, system will show the default appearance for different device type.

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@BuilderParam  customPicker?: CustomBuilder--><!--Device-AVCastPicker-@BuilderParam  customPicker?: CustomBuilder-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## normalColor

```TypeScript
@PropRef
  normalColor?: Color | int | string
```

正常状态下投播组件的颜色。 未设置时，将采用colorMode下的颜色设置。

**类型：** [Color](arkts-na-enums-color-e.md) \| int \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@PropRef  normalColor?: Color | int | string--><!--Device-AVCastPicker-@PropRef  normalColor?: Color | int | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## onStateChange

```TypeScript
onStateChange?: OnPickerStateCallback
```

投播状态更改回调。

**类型：** [OnPickerStateCallback](arkts-na-onpickerstatecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-onStateChange?: OnPickerStateCallback--><!--Device-AVCastPicker-onStateChange?: OnPickerStateCallback-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## pickerStyle

```TypeScript
@PropRef
  pickerStyle?: AVCastPickerStyle
```

投播样式。 - 当sessionType是audio或者video时，默认值为STYLE_PANEL。 - 当sessionType是voice_call或者video_call时，默认值为STYLE_MENU，且不可修改为STYLE_PANEL。

**类型：** [AVCastPickerStyle](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpickerparam-avcastpickerstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@PropRef  pickerStyle?: AVCastPickerStyle--><!--Device-AVCastPicker-@PropRef  pickerStyle?: AVCastPickerStyle-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## sessionType

```TypeScript
@PropRef
  sessionType?: string
```

会话类型，可参考[AVSessionType](../../apis-avsession-kit/arkts-apis/arkts-avsession-avsession-avsessiontype-t.md)。默认值为当前应用创建的AVSessionType。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AVCastPicker-@PropRef  sessionType?: string--><!--Device-AVCastPicker-@PropRef  sessionType?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

