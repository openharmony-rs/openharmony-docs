# MaximizeOptions

最大化窗口时的可选配置。

**起始版本：** 26.0.0

<!--Device-window-interface MaximizeOptions--><!--Device-window-interface MaximizeOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## acrossDisplayPresentation

```TypeScript
acrossDisplayPresentation?: AcrossDisplayPresentation
```

参数控制主窗口的瀑布模式策略。该参数只能在具有折叠功能的2in1设备上正确调用。如果在其他设备类型上调用，则没有任何效果。

**类型：** AcrossDisplayPresentation

**默认值：** AcrossDisplayPresentation.FOLLOW_ACROSS_DISPLAY_SETTING

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaximizeOptions-acrossDisplayPresentation?: AcrossDisplayPresentation--><!--Device-MaximizeOptions-acrossDisplayPresentation?: AcrossDisplayPresentation-End-->

**系统能力：** SystemCapability.Window.SessionManager

## maximizePresentation

```TypeScript
maximizePresentation?: MaximizePresentation
```

窗口最大化时的布局。

**类型：** MaximizePresentation

**默认值：** MaximizePresentation.ENTER_IMMERSIVE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaximizeOptions-maximizePresentation?: MaximizePresentation--><!--Device-MaximizeOptions-maximizePresentation?: MaximizePresentation-End-->

**系统能力：** SystemCapability.Window.SessionManager

## snapshotAnimationConfig

```TypeScript
snapshotAnimationConfig?: WindowSnapshotAnimationConfig
```

截图动效的配置。如果未指定，将使用系统默认动效。当持续时间和延迟参数都设置为0时，表示截图动效被取消。

**类型：** WindowSnapshotAnimationConfig

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaximizeOptions-snapshotAnimationConfig?: WindowSnapshotAnimationConfig--><!--Device-MaximizeOptions-snapshotAnimationConfig?: WindowSnapshotAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

