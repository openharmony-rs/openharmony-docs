# getUninstallDisposedRule（系统接口）

## getUninstallDisposedRule

```TypeScript
function getUninstallDisposedRule(appIdentifier: string, appIndex?: number): UninstallDisposedRule
```

��ȡָ��Ӧ�û����Ӧ�������õ����ȼ���ߵ�ж�ش��ù���

**起始版本：** 15

**需要权限：** ohos.permission.GET_DISPOSED_APP_STATUS or ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appIdentifier | string | 是 | Ҫ��ȡж�ش��ù����Ӧ�õ�appIdentifier��<br/>���Ӧ��û��appIdentifier��ʹ��appId���档appId��Ӧ�õ�Ψһ��ʶ����Ӧ��<br/>Bundle���ƺ�ǩ����Ϣ��������ȡ�����μ�[��ȡӦ�õ�appId](../../../../quick-start/common-problem-of-application.md#��λ�ȡӦ����Ϣ�е�appid)�� |
| appIndex | number | 否 | ��ʾ����Ӧ�õ�������Ĭ��ֵΪ0��<br/>appIndexΪ0ʱ����ʾ��ȡ��Ӧ�õ�ж�ش��ù���appIndex����0ʱ����ʾ��ȡָ������Ӧ�õ�ж�ش��ù��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| UninstallDisposedRule | ��ʾӦ�õ�ж�ش��ù��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex is not in the valid range. |
| [17700074](../../errorcode-universal.md#17700074-The) | The specified appIdentifier is invalid. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appIdentifier = "com.example.myapplication_xxxxx";

try {
  let data = appControl.getUninstallDisposedRule(appIdentifier, 1);
  console.info('getUninstallDisposedRule successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getUninstallDisposedRule failed ' + message);
}

```

