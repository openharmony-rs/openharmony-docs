# showAlertBeforeBackPage

## 导入模块

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="showalertbeforebackpage"></a>
## showAlertBeforeBackPage

```TypeScript
function showAlertBeforeBackPage(options: EnableAlertOptions): void
```

开启页面返回询问对话框。

> **说明：**  
>  
> - 从API version 9开始支持，从API version 18开始废弃，建议使用  
> [showAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#showalertbeforebackpage-1)替代。showAlertBeforeBackPage需先  
> 通过[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)获取  
> [Router](arkts-arkui-uicontext.md)实例，然后通过该实例进行调用。  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getRouter](docroot://reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)方法获取当前UI上下文关联的  
> [Router](arkts-arkui-uicontext.md)对象。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [showAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#showalertbeforebackpage-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function showAlertBeforeBackPage(options: EnableAlertOptions): void--><!--Device-router-function showAlertBeforeBackPage(options: EnableAlertOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EnableAlertOptions](arkts-arkui-router-enablealertoptions-i.md) | 是 | 文本弹窗信息描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.getUIContext().getRouter().showAlertBeforeBackPage({
    message: 'Message Info'
  });
} catch (err) {
  console.error(`showAlertBeforeBackPage failed. Code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}

```

