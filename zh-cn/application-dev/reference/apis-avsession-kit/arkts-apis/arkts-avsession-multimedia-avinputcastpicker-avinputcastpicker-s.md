# AVInputCastPicker

录音设备选择组件，可用于切换音频输入设备。 该组件为自定义组件，开发者在使用前需要先了解[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-unnamed-export declare struct AVInputCastPicker--><!--Device-unnamed-export declare struct AVInputCastPicker-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## customPicker

```TypeScript
@Prop
  customPicker?: CustomBuilder
```

自定义样式。建议开发者自定义组件样式，可有效提升组件渲染性能。

**类型：** CustomBuilder

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVInputCastPicker-@Prop  customPicker?: CustomBuilder--><!--Device-AVInputCastPicker-@Prop  customPicker?: CustomBuilder-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## onStateChange

```TypeScript
onStateChange?: OnPickerStateCallback
```

设备列表状态变更回调。

**类型：** [OnPickerStateCallback](arkts-avsession-onpickerstatecallback-t.md)

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback--><!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

