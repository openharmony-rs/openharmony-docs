# AVCastPickerOptions

拉起的投播组件包含的配置属性。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-avSession-interface AVCastPickerOptions--><!--Device-avSession-interface AVCastPickerOptions-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## menuPosition

```TypeScript
menuPosition?: MenuPosition
```

当pickerStyle设置为STYLE\_MENU时，可以设置弹出菜单的位置。

**类型：** MenuPosition

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-AVCastPickerOptions-menuPosition?: MenuPosition--><!--Device-AVCastPickerOptions-menuPosition?: MenuPosition-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## pickerStyle

```TypeScript
pickerStyle?: AVCastPickerStyle
```

设置组件样式。

**类型：** AVCastPickerStyle

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为24。

<!--Device-AVCastPickerOptions-pickerStyle?: AVCastPickerStyle--><!--Device-AVCastPickerOptions-pickerStyle?: AVCastPickerStyle-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## sessionType

```TypeScript
sessionType?: AVSessionType
```

会话类型，默认值为audio。 当前仅支持的会话类型有audio和video。如果传入voice\_call或video\_call，将默认按照传入audio处理。

**类型：** AVSessionType

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastPickerOptions-sessionType?: AVSessionType--><!--Device-AVCastPickerOptions-sessionType?: AVSessionType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

