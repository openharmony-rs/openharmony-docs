# AVInputCastPicker

录音设备选择组件，可用于切换音频输入设备。 该组件为自定义组件，开发者在使用前需要先了解[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare struct AVInputCastPicker--><!--Device-unnamed-export declare struct AVInputCastPicker-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## build

```TypeScript
@Builder
  build(): void
```

构造组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-AVInputCastPicker-@Builder  build(): void--><!--Device-AVInputCastPicker-@Builder  build(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## customPicker

```TypeScript
@BuilderParam
  customPicker?: CustomBuilder
```

自定义样式。建议开发者自定义组件样式，可有效提升组件渲染性能。 If not set, system will show the default appearance for different device type.

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-AVInputCastPicker-@BuilderParam  customPicker?: CustomBuilder--><!--Device-AVInputCastPicker-@BuilderParam  customPicker?: CustomBuilder-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## onStateChange

```TypeScript
onStateChange?: OnPickerStateCallback
```

设备列表状态变更回调。

**类型：** [OnPickerStateCallback](../../apis-avsession-kit/arkts-apis/arkts-avsession-onpickerstatecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback--><!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

