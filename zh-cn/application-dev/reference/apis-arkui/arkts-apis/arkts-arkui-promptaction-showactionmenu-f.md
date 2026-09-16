# showActionMenu

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>): void
```

创建并显示操作菜单，菜单响应结果使用callback异步回调返回。

> **说明：** 
> 
> - 从API version 9开始支持，从API version 18开始废弃，建议使用showActionMenu替代。 showActionMenu需先通过UIContext中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> - 从API version 11开始，可以通过使用UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showActionMenu

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | 是 | 操作菜单选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | 是 | 回调函数。弹出操作菜单成功时，err为undefined，data为获取到的操作菜单响应结果；失败时，err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例**

```TypeScript
showActionMenu(options: ActionMenuOptions, callback: AsyncCallback<ActionMenuSuccessResponse>):void

创建并显示操作菜单，菜单响应结果使用callback异步回调返回。

> 说明：
> 
> 从API version 9开始支持，从API version 18开始废弃，建议使用showActionMenu替代。showActionMenu需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> 从API version 11开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-apis-uicontext-promptaction.md)对象。

原子化服务API： 从API version 11开始，该接口支持在原子化服务中使用。

系统能力： SystemCapability.ArkUI.ArkUI.Full。

参数：

错误码：

以下错误码的详细介绍请参见[通用错误码](../../errorcode-universal.md)和[接口调用异常错误码](../errorcode-internal.md)。

示例：1
```

```TypeScript


示例：2

从API version 19开始，该示例通过调用ActionMenuOptions中的onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性展示了操作菜单生命周期相关接口的使用方法。
```

```TypeScript
showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>

创建并显示操作菜单，菜单响应后通过Promise返回结果。

> 说明：
> 
> 从API version 9开始支持，从API version 18开始废弃，建议使用showActionMenu替代。showActionMenu需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-apis-uicontext-promptaction.md)对象。

原子化服务API： 从API version 11开始，该接口支持在原子化服务中使用。

系统能力： SystemCapability.ArkUI.ArkUI.Full

参数：

返回值：

错误码：

以下错误码的详细介绍请参见[通用错误码](../../errorcode-universal.md)和[接口调用异常错误码](../errorcode-internal.md)。
```


## showActionMenu

```TypeScript
function showActionMenu(options: ActionMenuOptions): Promise<ActionMenuSuccessResponse>
```

创建并显示操作菜单，菜单响应后通过Promise返回结果。

> **说明：** 
> 
> - 从API version 9开始支持，从API version 18开始废弃，建议使用showActionMenu替代。 showActionMenu需先通过UIContext中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> - 从API version 10开始，可以通过使用UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showActionMenu

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | 是 | 操作菜单选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md)&gt; | Promise对象，返回菜单的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例**

参见 [showActionMenu](#showactionmenu)
