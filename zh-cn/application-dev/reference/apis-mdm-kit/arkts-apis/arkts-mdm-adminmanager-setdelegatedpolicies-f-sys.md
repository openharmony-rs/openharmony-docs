# setDelegatedPolicies（系统接口）

## setDelegatedPolicies

```TypeScript
function setDelegatedPolicies(bundleName: string, accountId: number, policies: Array<string>): void
```

ί������Ӧ���������豸�Ĺܿز��ԡ���ί�е�����Ӧ��������ί�в��Զ�Ӧ�ӿ�����Ȩ�ޡ�

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��Ҫ��ί�еĹ���Ӧ�õİ�������ί��Ӧ�õķַ�������Ϊenterprise_normal��enterprise_mdm������ͨ��<br/>[bundleManager.getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)<br/>�ӿڲ�ѯӦ��������BundleInfo������BundleInfo.appInfo.appDistributionTypeΪӦ�õķַ����͡� |
| accountId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0������ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1) |
| policies | Array&lt;string&gt; | 是 | [ί�в����б�](../../../../reference/apis-mdm-kit/js-apis-enterprise-adminManager.md#��ί�в����б�)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200009](../../errorcode-universal.md#9200009-Failed) | Failed to grant the permission to the application. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

// 需根据实际情况进行替换
let bundleName = 'com.example.myapplication';
let userId = 100;
let policies: Array<string> = ["disabled_hdc"];

try {
  adminManager.setDelegatedPolicies(bundleName, userId, policies);
  console.info(`Succeeded in setting delegated policies.`);
} catch (err) {
  console.error(`Failed to set delegated policies. Code: ${err.code}, message: ${err.message}`);
}

```

