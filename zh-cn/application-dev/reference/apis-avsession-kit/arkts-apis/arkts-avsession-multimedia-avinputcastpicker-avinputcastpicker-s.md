# AVInputCastPicker

录音设备选择组件，可用于切换音频输入设备。

该组件为自定义组件，开发者在使用前需要先了解[@Component](docroot://ui/state-management/arkts-create-custom-components.md#component)。

**起始版本：** 20

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AVInputCastPicker--><!--Device-unnamed-export declare struct AVInputCastPicker-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## 导入模块

```TypeScript
import { AVInputCastPicker } from '@kit.AVSessionKit';
```

## customPicker

```TypeScript
customPicker?: CustomBuilder
```

自定义样式。建议开发者自定义组件样式，可有效提升组件渲染性能。

**类型：** CustomBuilder

**起始版本：** 20

**装饰器类型：** @Prop

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVInputCastPicker-customPicker?: CustomBuilder--><!--Device-AVInputCastPicker-customPicker?: CustomBuilder-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

## onStateChange

```TypeScript
onStateChange?: OnPickerStateCallback
```

设备列表状态变更回调。

**类型：** OnPickerStateCallback

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback--><!--Device-AVInputCastPicker-onStateChange?: OnPickerStateCallback-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVInputCast

