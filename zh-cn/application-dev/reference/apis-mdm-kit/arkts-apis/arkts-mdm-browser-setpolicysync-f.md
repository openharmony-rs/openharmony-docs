# setPolicySync

## setPolicySync

```TypeScript
function setPolicySync(admin: Want, appId: string, policyName: string, policyValue: string): void
```

Ϊָ�������������������Ӳ��ԡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_SET_BROWSER_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appId | string | 是 | Ӧ��appId������ָ�����������ʾӦ�õ�Ψһ��ʶ��������Ϣ�ɲο�<br/>[ʲô��appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| policyName | string | 是 | ������Ӳ��������ɽӿڵ��÷���ָ�������Լ��������ֵΪ���ַ���ʱ����ʾ����Ӧ��appId��Ӧ����������ԡ� |
| policyValue | string | 是 | ������Ӳ���ֵ���ɽӿڵ��÷���ָ�������Լ��������ֵΪ���ַ���ʱ����ʾȡ���������������Ӧ������Ӳ��ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { browser } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 此处参数appId的赋值应替换为开发者自己指定的浏览器的应用ID
let appId: string = 'com.example.******_******/******5t5CoBM=';
let policyName: string = 'InsecurePrivateNetworkRequestsAllowed';
let policyValue: string = '{"level":"mandatory","scope":"machine","source":"platform","value":true}';

try {
  browser.setPolicySync(wantTemp, appId, policyName, policyValue);
  console.info('Succeeded in setting browser policies.');
} catch (err) {
  console.error(`Failed to set browser policies. Code is ${err.code}, message is ${err.message}`);
}

```

