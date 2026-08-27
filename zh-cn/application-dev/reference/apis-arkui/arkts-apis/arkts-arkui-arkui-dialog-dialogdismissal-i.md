# DialogDismissal

提供有关关闭对话框的操作的信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## dismiss

```TypeScript
dismiss: VoidCallback
```

关闭对话框的回调。只有当需要退出对话框时，才会调用此接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

无法关闭对话框的原因。

**类型：** [DismissReason](../arkts-components/arkts-arkui-dismissreason-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
