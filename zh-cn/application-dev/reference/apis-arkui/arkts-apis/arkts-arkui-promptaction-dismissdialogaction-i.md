# DismissDialogAction

Dialog关闭的信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## dismiss

```TypeScript
dismiss: Callback<void>
```

Dialog关闭回调函数。开发者需要退出时调用，不需要退出时无需调用。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reason

```TypeScript
reason: DismissReason
```

触发Dialog关闭的操作类型（如点击遮障层、按返回键等）。开发者可根据reason判断用户的具体关闭操作，决定是否调用dismiss()关闭Dialog。

**类型：** [DismissReason](../arkts-components/arkts-arkui-dismissreason-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
