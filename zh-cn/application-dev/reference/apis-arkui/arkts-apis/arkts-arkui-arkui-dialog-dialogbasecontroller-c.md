# DialogBaseController

用于控制对话框的类。

**起始版本：** 26.1.0

<!--Device-unnamed-export class DialogBaseController--><!--Device-unnamed-export class DialogBaseController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DialogButtonOrientation, DialogState, DialogResult, DialogBaseController, DialogBaseAlignment, DialogDismissal } from '@kit.ArkUI';
```

## close

```TypeScript
close(): void
```

关闭相应的对话框。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogBaseController-close(): void--><!--Device-DialogBaseController-close(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogBaseController-constructor()--><!--Device-DialogBaseController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getState

```TypeScript
getState(): DialogState
```

获取状态。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-DialogBaseController-getState(): DialogState--><!--Device-DialogBaseController-getState(): DialogState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DialogState](arkts-arkui-arkui-dialog-dialogstate-e.md) | 返回状态。 |

