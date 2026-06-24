# getDelegatedPolicies

## getDelegatedPolicies

```TypeScript
function getDelegatedPolicies(admin: Want, bundleName: string): Array<string>
```

��ѯ��ί��Ӧ�ÿɷ��ʵĲ����б���

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_DELEGATED_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ��ί��Ӧ�ð�������ί��Ӧ�õķַ�������Ϊenterprise_normal��enterprise_mdm������ͨ��<br/>[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)�ӿ�<br/>��ѯӦ��������[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md#BundleInfo)������BundleInfo.appInfo.appDistributionTypeΪӦ�õķַ����͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ί�в����б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let admin: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let policies: Array<string> = adminManager.getDelegatedPolicies(admin, "com.example.enterprise.xxx");
  console.info(`Succeeded in getting delegated policies.${JSON.stringify(policies)}`);
} catch (err) {
  console.error(`Failed to get delegated policies. Code: ${err.code}, message: ${err.message}`);
}

```

