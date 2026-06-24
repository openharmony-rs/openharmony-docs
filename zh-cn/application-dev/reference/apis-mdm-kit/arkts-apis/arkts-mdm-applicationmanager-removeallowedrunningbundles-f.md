# removeAllowedRunningBundles

## removeAllowedRunningBundles

```TypeScript
function removeAllowedRunningBundles(admin: Want, appIdentifiers: Array<string>, accountId: number): void
```

��Ӧ�ô�ָ���û��µ�Ӧ�����������������Ƴ���

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIdentifiers | Array&lt;string&gt; | 是 | Ӧ��Ψһ��ʶ�������顣����ͨ���ӿ�bundleManager.getInstalledBundleList��ȡbundleInfo.signatureInfo.appIdentifier��ȡֵ��Χ�����鳤�Ȳ��ܳ���200��<br/><br/>��󳤶�Ϊ200�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>-<br/>�û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�getOsAccountLocalId�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
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
  applicationManager.removeAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in removing allowed running bundles.');
} catch (err) {
  console.error(`Failed to remove allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}

```

