# showAlertBeforeBackPage

## showAlertBeforeBackPage

```TypeScript
function showAlertBeforeBackPage(options: EnableAlertOptions): void
```

����ҳ�淵��ѯ�ʶԻ���

> **˵����**
>
> - ��API version 9��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [showAlertBeforeBackPage](arkts-arkui-router-c.md#showAlertBeforeBackPage-1)�����showAlertBeforeBackPage����
> ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** [showAlertBeforeBackPage](arkts-arkui-router-c.md#showAlertBeforeBackPage-1)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | EnableAlertOptions | 是 | �ı�������Ϣ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.getUIContext().getRouter().showAlertBeforeBackPage({
    message: 'Message Info'
  });
} catch (err) {
  console.error(`showAlertBeforeBackPage failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
}

```

