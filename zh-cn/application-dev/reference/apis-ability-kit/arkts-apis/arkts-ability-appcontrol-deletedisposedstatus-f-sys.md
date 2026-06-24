# deleteDisposedStatus（系统接口）

## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void
```

ɾ��Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | Ҫɾ�����ع����Ӧ�õ�appId��appIdentifier��ʹ��appId���õ����ع���ֻ��ͨ��appIdɾ����ʹ��appIdentifier���õ�ͬ����<br/><br/>**˵����**<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)��<br/><br/>[appIdentifier](arkts-ability-signatureinfo-i.md#SignatureInfo)Ҳ��Ӧ�õ�Ψһ��ʶ��������Ϣ�ɲο�<br/>[ʲô��appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����ȡ�����μ�<br/>[��ȡӦ�õ�appIdentifier](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appidentifier)�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص������������ô���״̬�ɹ�ʱ��err����null������ص��������ؾ��������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700005](../../errorcode-universal.md#17700005-The) | The specified app ID is empty string. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";
try {
  appControl.deleteDisposedStatus(appId, (error: BusinessError, data) => {
    if (error) {
      console.error('deleteDisposedStatus failed ' + error.message);
      return;
    }
    console.info('deleteDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}

```


## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string): Promise<void>
```

ɾ��Ӧ�õĴ���״̬��ʹ��promise�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | Ҫɾ�����ع����Ӧ�õ�appId��appIdentifier��ʹ��appId���õ����ع���ֻ��ͨ��appIdɾ����ʹ��appIdentifier���õ�ͬ����<br/><br/>**˵����**<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)��<br/><br/>[appIdentifier](arkts-ability-signatureinfo-i.md#SignatureInfo)Ҳ��Ӧ�õ�Ψһ��ʶ��������Ϣ�ɲο�<br/>[ʲô��appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����ȡ�����μ�<br/>[��ȡӦ�õ�appIdentifier](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appidentifier)�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700005](../../errorcode-universal.md#17700005-The) | The specified app ID is empty string. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.deleteDisposedStatus(appId)
    .then(() => {
      console.info('deleteDisposedStatus success');
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('deleteDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}

```

