# setDisposedStatus（系统接口）

## setDisposedStatus

```TypeScript
function setDisposedStatus(appId: string, disposedWant: Want, callback: AsyncCallback<void>): void
```

����Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | ��Ҫ���ô��õ�Ӧ�õ�appId��<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)�� |
| disposedWant | Want | 是 | ��Ӧ�õĴ�����ͼ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص������������ô���״̬�ɹ���errΪnull������Ϊ������� |

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
import { Want } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = { bundleName: 'com.example.myapplication' };

try {
  appControl.setDisposedStatus(appId, want, (error: BusinessError, data) => {
    if (error) {
      let message = (error as BusinessError).message;
      console.error('setDisposedStatus failed ' + message);
      return;
    }
    console.info('setDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedStatus failed ' + message);
}

```


## setDisposedStatus

```TypeScript
function setDisposedStatus(appId: string, disposedWant: Want): Promise<void>
```

����Ӧ�õĴ���״̬��ʹ��Promise�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | ��Ҫ���ô���״̬��Ӧ�õ�appId��<br/>appId��Ӧ�õ�Ψһ��ʶ����Ӧ��Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�<br/>[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)�� |
| disposedWant | Want | 是 | ��Ӧ�õĴ�����ͼ�� |

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
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { appControl } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = { bundleName: 'com.example.myapplication' };

try {
  appControl.setDisposedStatus(appId, want)
    .then(() => {
      console.info('setDisposedStatus success');
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('setDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedStatus failed ' + message);
}

```

