# enableAlertBeforeBackPage

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

## enableAlertBeforeBackPage

```TypeScript
function enableAlertBeforeBackPage(options: EnableAlertOptions): void
```

开启页面返回询问对话框。调用此方法后，执行back返回页面时将弹出确认对话框，用户确认后才执行页面返回操作。 适用于需要防止用户误操作返回导致数据丢失的场景，例如用户正在填写表单、编辑文档或进行支付操作时，弹出确认对话框以避免意外退出。 > **说明：** > > 从API version 8开始支持，从API version 9开始废弃，建议使用 > [showAlertBeforeBackPage](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-router-c.md#showalertbeforebackpage)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [showAlertBeforeBackPage](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-router-c.md#showalertbeforebackpage)

<!--Device-router-function enableAlertBeforeBackPage(options: EnableAlertOptions): void--><!--Device-router-function enableAlertBeforeBackPage(options: EnableAlertOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | 是 | 文本弹窗信息描述。 |

**示例**

```TypeScript
import { router } from '@kit.ArkUI';

router.enableAlertBeforeBackPage({
  message: 'Message Info'
});
```

