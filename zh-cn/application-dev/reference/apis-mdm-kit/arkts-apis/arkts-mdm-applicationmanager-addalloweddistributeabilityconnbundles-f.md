# addAllowedDistributeAbilityConnBundles

## addAllowedDistributeAbilityConnBundles

```TypeScript
function addAllowedDistributeAbilityConnBundles(admin: Want, appIdentifiers: Array<string>, serviceType: ServiceType, accountId: number): void
```

Ϊָ���û���������ʹ�÷ֲ�ʽ������Ӧ�������������е�Ӧ����ָ���û��¿���ʹ��ָ���ķֲ�ʽ������

��ǰ֧�ֵķֲ�ʽ�����У�[Эͬ����](arkts-mdm-applicationmanager-servicetype-e.md#ServiceType)��

> **˵����**
>
> 1.���Ҫ��������ʹ��Эͬ�����Ӧ���������ڵ��ñ��ӿ�ǰ�����Ѿ�ͨ��
> [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)
> �ӿڽ������������豸�������ݵ��豸�䵥�������ݵ�������������׳�������9201043��

> 2.���������豸�������ݵ��豸�䵥�������ݵ��������������ʱ��ͨ�����ӿ����õ�����ʹ��Эͬ�����Ӧ�������ᱻͬ�������

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
| [9201043](../../errorcode-universal.md#9201043-Prerequisites) | Prerequisites for the API call have not been satisfied. For example,<br/>distributed outgoing transmission is not disallowed before adding the distributed bidirectional collaboration<br/>trustlist. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 如果要在100用户下，禁止设备上除了指定应用以外的其他应用向其他设备传输数据，需要执行两个步骤：
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let accountId: number = 100;

// 步骤1. 禁用100用户下的设备间单向传输数据能力（若之前已经设置过设备间单向传输数据能力的禁用，此处无需重复设置）
try {
  restrictions.setDisallowedPolicyForAccount(wantTemp, 'distributedTransmissionOutgoing', true, accountId);
  console.info('Succeeded in setting distributedTransmissionOutgoing disabled');
} catch (err) {
  console.error(`Failed to set distributedTransmissionOutgoing disabled. Code is ${err.code}, message is ${err.message}`);
}

// 步骤2. 设置100用户下允许使用某种分布式业务（例如协同业务）的应用名单
try {
  // 需根据实际情况进行替换
  let appIdentifiers: Array<string> = ['6917****3569'];
  applicationManager.addAllowedDistributeAbilityConnBundles(wantTemp, appIdentifiers, applicationManager.ServiceType.COLLABORATION_SERVICE, accountId);
  console.info('Succeeded in adding allowed distribute ability conn bundles.');
} catch(err) {
  console.error(`Failed to add allowed distribute ability conn bundles. Code: ${err.code}, message: ${err.message}`);
}
// 执行以上两个步骤后，在100用户下，仅应用6917****3569可以通过协同业务向其他设备传输数据，其他应用无法向其他设备传输数据。
// 注意：禁用某用户下的设备间单向传输数据能力后，是否需要添加允许使用协同业务的应用名单，应根据实际业务需求判断。

```

