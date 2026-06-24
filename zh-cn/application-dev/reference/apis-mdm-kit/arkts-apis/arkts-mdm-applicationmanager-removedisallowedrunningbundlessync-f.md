# removeDisallowedRunningBundlesSync

## removeDisallowedRunningBundlesSync

```TypeScript
function removeDisallowedRunningBundlesSync(admin: Want, appIds: Array<string>, accountId?: number): void
```

��Ӧ�ôӵ�ǰ/ָ���û��µ�Ӧ�����н�ֹ�������Ƴ���

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���飬ָ������Ӧ�á�<br/>**˵����** ��API version 21�汾��ʼ�������е�Ԫ��֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�����Ƴ������<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���������Ƴ�ͬһӦ�õ�<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����API version 20��֮ǰ�汾�������е�Ԫ��ֻ֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| accountId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ��<br/><br/>- ���ýӿ�ʱ��������accountId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����accountId����ʾ��ǰ�û��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  applicationManager.removeDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in removing disallowed running bundles.');
} catch (err) {
  console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}

```

