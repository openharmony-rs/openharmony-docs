# ArcButton

弧形按钮组件提供强调、普通、警告等样式按钮，推荐用于圆形屏幕的设备。
> **说明：**
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

**起始版本：** 18

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct ArcButton--><!--Device-unnamed-export declare struct ArcButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcButtonPosition, ArcButton, ArcButtonStatus, ArcButtonStyleMode, ArcButtonOptions, ArcButtonProgressConfig } from '@kit.ArkUI';
```

## options

```TypeScript
readonly options: ArcButtonOptions
```

定义ArcButton组件的文本、背景色、阴影等参数。

**类型：** ArcButtonOptions

**起始版本：** 18

**装饰器类型：** @Require

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcButton-readonly options: ArcButtonOptions--><!--Device-ArcButton-readonly options: ArcButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

