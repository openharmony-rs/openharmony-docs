# installMarketApps

## installMarketApps

```TypeScript
function installMarketApps(admin: Want, bundleNames: Array<string>): void
```

���ز���װӦ���г�Ӧ�á�

> **˵����**
>
> ���ӿڵ��óɹ����������������Ӧ���������񣬴��������Ӧ���г���������������һ�¡����ذ�װ�����󣬰�װ�����ͨ���ص�
> [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](> **˵��**
>
���ӿڵ��óɹ����������������Ӧ���������񣬴��������Ӧ���г���������������һ�¡����ذ�װ�����󣬰�װ�����ͨ���ص�[EnterpriseAdminExtensionAbility.onMarketAppInstallResult
]{@link

**起始版本：** 22

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the<br/>EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | 是 | Ӧ�ð����б���һ����ഫ��10������������Ӧ���г��а���һ�£������޷������������񣬲��׳�������9201002�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201002](../../errorcode-universal.md#9201002-Failed) | Failed to install the application. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want ) from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleNames: Array<string> = [ 'com.huaweicloud.m' ];
try {
  bundleManager.installMarketApps(wantTemp, bundleNames);
  console.info(`Succeeded in installing market apps.`);
} catch(err) {
  console.error(`Failed to install market apps. Code: ${err.code}, message: ${err.message}`);
}

```

