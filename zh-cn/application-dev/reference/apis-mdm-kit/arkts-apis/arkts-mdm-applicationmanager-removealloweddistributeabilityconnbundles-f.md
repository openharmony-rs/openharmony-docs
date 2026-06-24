# removeAllowedDistributeAbilityConnBundles

## removeAllowedDistributeAbilityConnBundles

```TypeScript
function removeAllowedDistributeAbilityConnBundles(admin: Want, appIdentifiers: Array<string>, serviceType: ServiceType, accountId: number): void
```

Ϊָ���û��Ƴ�����ʹ�÷ֲ�ʽ������Ӧ���������Ƴ����������л���ʣ���Ӧ�ã���������е�Ӧ����ָ���û��¿���ʹ��ָ�����͵ķֲ�ʽ���������������ѱ���գ���ʣ���Ӧ�ã�������Ӧ����ָ���û��¶�������ʹ��ָ�����͵ķֲ�ʽ������

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIdentifiers | Array&lt;string&gt; | 是 | Ӧ��[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)�����飬����ͨ���ӿ�<br/>[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3)<br/>��ȡbundleInfo.signatureInfo.appIdentifier�������б��������ܳ���200���� |
| serviceType | ServiceType | 是 | �ֲ�ʽ�������͡� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��������<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

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
  let appIdentifiers: Array<string> = ['6917****3569'];
  let accountId: number = 100;
  applicationManager.removeAllowedDistributeAbilityConnBundles(wantTemp, appIdentifiers, applicationManager.ServiceType.COLLABORATION_SERVICE, accountId);
  console.info('Succeeded in removing allowed distribute ability conn bundles.');
  // 注意：移除用户下允许使用协同业务的应用名单后，是否需要解除禁用该用户下的设备间单向传输数据能力，应根据实际业务需求判断。
} catch(err) {
  console.error(`Failed to remove allowed distribute ability conn bundles. Code: ${err.code}, message: ${err.message}`);
}

```

