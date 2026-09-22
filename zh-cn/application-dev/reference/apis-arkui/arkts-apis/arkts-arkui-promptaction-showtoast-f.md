# showToast

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Creates and displays a toast.

创建并显示即时反馈。

> **说明：** 
> 
> - 从API version 9开始支持，从API version 18开始废弃，建议使用[showToast](arkts-arkui-arkui-uicontext-promptaction-c.md#showtoast)替代。 showToast需先通过UIContext中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象，然后通过该对象进行调用。且直接使用showToast可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> - 从API version 10开始，可以通过使用UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象。
> 
> - Toast样式单一，不支持内容的自定义，具体支持能力请参考ShowToastOptions提供的接口。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showToast

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例**

showToast(options: ShowToastOptions): void

创建并显示即时反馈。

> 说明：
> 
> 从API version 9开始支持，从API version 18开始废弃，建议使用showToast替代。showToast需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showToast可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-apis-uicontext-promptaction.md)对象。
> 
> Toast样式单一，不支持内容的自定义，具体支持能力请参考ShowToastOptions提供的接口。

原子化服务API： 从API version 11开始，该接口支持在原子化服务中使用。

系统能力： SystemCapability.ArkUI.ArkUI.Full

参数：

错误码：

以下错误码的详细介绍请参见[通用错误码](../../errorcode-universal.md)和[接口调用异常错误码](../errorcode-internal.md)。

> 说明：
> 
> 当返回100001错误码时，可能出现了UI上下文不明确的问题，对此可以使用UIContext中的接口进行替换，详细说明可参考[使用UI上下文接口操作界面](../../../ui/arkts-global-interface.md)。

```TypeScript
import { promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct toastExample {
  build() {
    Column() {
      Button('Show toast').fontSize(20)
        .onClick(() => {
          try {
            promptAction.showToast({
              message: 'Hello World',
              duration: 2000,
              showMode:promptAction.ToastShowMode.DEFAULT,
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showToast args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```
