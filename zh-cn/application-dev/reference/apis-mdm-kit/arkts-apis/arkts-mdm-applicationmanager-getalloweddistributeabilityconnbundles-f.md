# getAllowedDistributeAbilityConnBundles

## getAllowedDistributeAbilityConnBundles

```TypeScript
function getAllowedDistributeAbilityConnBundles(admin: Want | null, serviceType: ServiceType, accountId: number): Array<string>
```

��ȡָ���û�������ʹ��ָ�����͵ķֲ�ʽ������Ӧ��������

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| serviceType | ServiceType | 是 | �ֲ�ʽ�������͡� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��������<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ����ʹ��ָ�����͵ķֲ�ʽ������Ӧ�õ�[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)�����顣 |

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

try {
  // 需根据实际情况进行替换
  let accountId: number = 100;
  let result: Array<string> = applicationManager.getAllowedDistributeAbilityConnBundles(wantTemp, applicationManager.ServiceType.COLLABORATION_SERVICE, accountId);
  console.info(`Succeeded in getting allowed distribute ability conn bundles: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get allowed distribute ability conn bundles. Code: ${err.code}, message: ${err.message}`);
}

```

