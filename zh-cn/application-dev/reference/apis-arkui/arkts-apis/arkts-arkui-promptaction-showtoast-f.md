# showToast

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

Creates and displays a toast.创建并显示即时反馈。

> **说明：**
> 
> - 从API version 9开始支持，从API version 18开始废弃，建议使用showToast替代。 showToast需先通过UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取[PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象， 然后通过该对象进行调用。且直接使用showToast可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题。
> 
> - 从API version 10开始，可以通过使用UIContext中的 [getPromptAction](arkts-arkui-arkui-uicontext-uicontext-c.md#getpromptaction)方法获取当前UI上下文关联的 [PromptAction](arkts-arkui-arkui-uicontext-promptaction-c.md)对象。
> 
> - Toast样式单一，不支持内容的自定义，具体支持能力请参考ShowToastOptions提供的接口。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** showToast

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ShowToastOptions | 是 | Toast选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例**

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
