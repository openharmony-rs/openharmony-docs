# closeCustomDialog

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## closeCustomDialog

```TypeScript
function closeCustomDialog(dialogId: number): void
```

关闭自定义弹窗。

> **说明：**
> 
> - 从API version 11开始支持，从API version 18开始废弃，建议使用closeCustomDialog替代。 closeCustomDialog需先通过UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取 [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象，然后通过该对象进行调用。且直接使用closeCustomDialog可能导致 [UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> - 从API version 12开始，可以通过使用UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的 [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象。

**起始版本：** 11

**废弃版本：** 18

**替代接口：** closeCustomDialog

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogId | number | 是 | openCustomDialog返回的对话框id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
