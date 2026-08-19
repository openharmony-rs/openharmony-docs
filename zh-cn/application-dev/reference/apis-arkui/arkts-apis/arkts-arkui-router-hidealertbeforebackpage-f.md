# hideAlertBeforeBackPage

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## hideAlertBeforeBackPage

```TypeScript
function hideAlertBeforeBackPage(): void
```

禁用页面返回询问对话框。调用此方法后，将关闭由showAlertBeforeBackPage 开启的返回询问对话框，back操作将不再弹出确认对话框，直接执行页面返回。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用 > [hideAlertBeforeBackPage](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-router-c.md#hidealertbeforebackpage)替代。hideAlertBeforeBackPage需先 > 通过[UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)中的 > [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取 > [Router](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)中的 > [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的 > [Router](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [hideAlertBeforeBackPage](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-router-c.md#hidealertbeforebackpage)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function hideAlertBeforeBackPage(): void--><!--Device-router-function hideAlertBeforeBackPage(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
this.getUIContext().getRouter().hideAlertBeforeBackPage();
```

