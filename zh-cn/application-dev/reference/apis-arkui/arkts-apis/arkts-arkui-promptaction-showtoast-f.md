# showToast

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Creates and displays a toast.

创建并显示即时反馈。

> **说明：**  
>  
> - 从API version 9开始支持，从API version 18开始废弃，建议使用[showToast](arkts-apis-uicontext-promptaction.md#showtoast)替代。showToast需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showToast可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的[PromptAction](arkts-apis-uicontext-promptaction.md)对象。  
>  
> - Toast样式单一，不支持内容的自定义，具体支持能力请参考[ShowToastOptions](#showtoastoptions)提供的接口。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showToast

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function showToast(options: ShowToastOptions): void--><!--Device-promptAction-function showToast(options: ShowToastOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

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
              duration: 2000
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
              duration: 2000
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

