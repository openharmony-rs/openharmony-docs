# DialogBaseOptions

所有Dialog类型共享的基本选项。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置对话框的变形动画模式。

**类型：** [DistortionMode](../arkts-components/arkts-arkui-distortionmode-e-sys.md)

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置对话框的edgeLight动画模式。

**类型：** [EdgeLightMode](../arkts-components/arkts-arkui-edgelightmode-e-sys.md)

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
