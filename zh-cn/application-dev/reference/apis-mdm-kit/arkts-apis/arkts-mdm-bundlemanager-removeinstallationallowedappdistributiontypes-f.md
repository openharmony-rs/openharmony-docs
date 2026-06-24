# removeInstallationAllowedAppDistributionTypes

## removeInstallationAllowedAppDistributionTypes

```TypeScript
function removeInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array<AppDistributionType>): void
```

�Ƴ�Ӧ�õķַ����͡���ֻ�Ƴ��������в��ֵķַ����ͣ���ǰ�豸���԰�װ������ʣ�µķַ����͵�Ӧ�ã����޷���װ
[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md#AppDistributionType)��δ���ӵķַ����͵�Ӧ�á�

Ӧ�ó���ǩ��֤��ķַ�������ϸ������μ�[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��appDistributionType���ԡ�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appDistributionTypes | Array&lt;AppDistributionType&gt; | 是 | Ӧ�ó���ǩ��֤��ķַ��������顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let appDistributionTypes: Array<bundleManager.AppDistributionType> = [bundleManager.AppDistributionType.APP_GALLERY];
  bundleManager.removeInstallationAllowedAppDistributionTypes(wantTemp, appDistributionTypes);
  console.info('Succeeded in removing allowed appDistributionTypes.');
} catch (err) {
  console.error(`Failed to remove allowed appDistributionTypes. Code: ${err.code}, message: ${err.message}`);
}

```

