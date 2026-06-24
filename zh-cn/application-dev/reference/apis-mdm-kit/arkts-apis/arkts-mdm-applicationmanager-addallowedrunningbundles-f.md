# addAllowedRunningBundles

## addAllowedRunningBundles

```TypeScript
function addAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void
```

����Ӧ����Ӧ��������������������������������Ӧ��������ָ���û������У���������������Ӧ�ò�������ָ���û������С�

> **˵����**
>

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIdentifiers | Array&lt;string&gt; | 是 | Ӧ��<br/>[Ψһ��ʶ��](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�����飬����ͨ���ӿ�<br/>[bundleManager.getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList-1)<br/>��ȡbundleInfo.signatureInfo.appIdentifier��<br/>ȡֵ��Χ��<br/>- �����û��¸������������ܳ���200������100�û����Ѿ�������50����101�û�δ���ã���100�û�������<br/>����150����101�û�����������200���� |
| accountId | number | 是 | ȡֵ��ΧΪȫ��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

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
let appIdentifiers: Array<string> = ['0123456789123456789'];

try {
  applicationManager.addAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in adding allowed running bundles.');
} catch (err) {
  console.error(`Failed to add allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}

```

