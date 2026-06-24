# getDisposedStatus（系统接口）

## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string, callback: AsyncCallback<Want>): void
```

��ȡָ��Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����Ӧ�õĴ���״̬��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | Ҫ��ѯ��Ӧ�õ�appId��<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)�� |
| callback | AsyncCallback&lt;Want&gt; | 是 | �ص�����������ȡӦ�õĴ���״̬�ɹ�ʱ��errΪnull��dataΪ��ȡ���Ĵ���״̬������Ϊ������� |

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
  appControl.getDisposedStatus(appId, (error, data) => {
    if (error) {
      let message = (error as BusinessError).message;
      console.error('getDisposedStatus failed ' + message);
      return;
    }
    console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}

```


## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string): Promise<Want>
```

��ȡָ��Ӧ�������õĴ���״̬��ʹ��Promise�첽�ص����ɹ�����Ӧ�õĴ���״̬��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | Ҫ��ѯ��Ӧ�õ�appId��<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | Promise���󣬷���Ӧ�õĴ���״̬�� |

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
  appControl.getDisposedStatus(appId)
    .then((data) => {
      console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('getDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}

```

