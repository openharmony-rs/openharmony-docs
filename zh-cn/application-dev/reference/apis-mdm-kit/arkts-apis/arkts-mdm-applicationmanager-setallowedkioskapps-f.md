# setAllowedKioskApps

## setAllowedKioskApps

```TypeScript
function setAllowedKioskApps(admin: Want, appIdentifiers: Array<string>): void
```

����������Kioskģʽ�����е�Ӧ�á�

KioskģʽΪϵͳ�����ṩ��һ��Ӧ������ģʽ����ģʽ�»Ὣ�豸�����ڵ���Ӧ�û���һ��Ӧ�����У�ͬʱ������״̬��״̬�������Ʋ����͹ؼ����ܽ��п��ƣ���ֹ�û����豸����������Ӧ�û�ִ������������

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_KIOSK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIdentifiers | Array&lt;string&gt; | 是 | Ӧ��[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)�����飬����ͨ���ӿ�<br/>[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3)<br/>��ȡbundleInfo.signatureInfo.appIdentifier���ظ�����ʱ�������õ�����Ḳ�Ǿɵ����ã��������200���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let appIdentifiers: Array<string> = ['6917****3569'];
  applicationManager.setAllowedKioskApps(wantTemp, appIdentifiers);
  console.info('Succeeded in setting allowed kiosk apps.');
} catch (err) {
  console.error(`Failed to set allowed kiosk apps. Code is ${err.code}, message is ${err.message}`);
}

```

