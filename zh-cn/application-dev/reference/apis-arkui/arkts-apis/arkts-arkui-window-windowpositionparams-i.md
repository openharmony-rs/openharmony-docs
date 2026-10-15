# WindowPositionParams

```TypeScript
interface WindowPositionParams
```

描述待调整z序的主窗口的位置。

**起始版本：** 26.0.1

<!--Device-window-interface WindowPositionParams--><!--Device-window-interface WindowPositionParams-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## insertAfter

```TypeScript
insertAfter: number
```

要调整到的位置。若该值大于0，则为另一个主窗口的ID，表示将目标窗口置于该主窗口下方；否则为[WindowPosition](arkts-arkui-window-windowposition-e.md)的哨兵值，用于将窗口置于所有应用主窗口的底部或顶部，或切换其全局置顶状态。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPositionParams-insertAfter: int--><!--Device-WindowPositionParams-insertAfter: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowId

```TypeScript
windowId: number
```

待调整z序的主窗口ID。该窗口必须是当前应用进程中的主窗口。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowPositionParams-windowId: int--><!--Device-WindowPositionParams-windowId: int-End-->

**系统能力：** SystemCapability.Window.SessionManager
