# deleteDisposedStatusSync（系统接口）

## deleteDisposedStatusSync

```TypeScript
function deleteDisposedStatusSync(appId: string, appIndex?: number): void
```

��ͬ������ɾ��ָ��Ӧ�û����Ӧ�õĴ���״̬���ɹ�����null��ʧ���׳���Ӧ�쳣��

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | Ҫɾ�����ع����Ӧ�õ�appId��appIdentifier��ʹ��appId���õ����ع���ֻ��ͨ��appIdɾ����ʹ��appIdentifier���õ�ͬ����<br/><br/>**˵����**<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)��<br/><br/>[appIdentifier](arkts-ability-signatureinfo-i.md#SignatureInfo)Ҳ��Ӧ�õ�Ψһ��ʶ��������Ϣ�ɲο�<br/>[ʲô��appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����ȡ�����μ�<br/>[��ȡӦ�õ�appIdentifier](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appidentifier)�� |
| appIndex | number | 否 | ��ʾ����Ӧ�õ�������Ĭ��ֵΪ0��<br/>appIndexΪ0ʱ����ʾɾ����Ӧ�õĴ���״̬��appIndex����0ʱ����ʾɾ��ָ������Ӧ�õĴ���״̬�� [since 12] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700005](../../errorcode-universal.md#17700005-The) | The specified app ID is invalid. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex is not in the valid range.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId: string = "com.example.myapplication_xxxxx";

try {
  appControl.deleteDisposedStatusSync(appId, 1);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatusSync failed ' + message);
}

```

