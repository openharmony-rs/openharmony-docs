# updateApn

## updateApn

```TypeScript
function updateApn(admin: Want, apnInfo: Record<string, string>, apnId: string): void
```

����APN��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| apnInfo | Record&lt;string, string&gt; | 是 | ��Ҫ���µ�APN������Ϣ��<br/>- apnName��APN���õ����Ʊ�ʶ������ѡ��<br/>- mcc��3λ���ֵ��ƶ����Ҵ��룬��ѡ��- mnc��2-3λ���ֵ��ƶ�������룬��ѡ��<br/>- APN����������ƣ���ѡ��<br/>- type��APN�ķ������ͣ���ѡ��<br/>- user��APN������֤���û�������ѡ��<br/>-<br/>password��APN������֤�����룬��ѡ��<br/>- proxy����ͨ�������ӵĴ�����������ַ����ѡ��<br/>- mmsproxy�����ŷ����ר�ô�����ַ����ѡ��<br/>- authType��APN����֤Э������<br/>����ѡ�� |
| apnId | string | 是 | ��Ҫ���µ�APN ID������ͨ��<br/>[networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md#queryApn-1)��ȡ�豸��Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // 需根据实际情况进行替换
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
let apnId: string = "1"; // 需根据实际情况进行替换
try {
  networkManager.updateApn(wantTemp, apnInfo, apnId);
  console.info(`Succeeded in updating apn.`);
} catch (err) {
  console.error(`Failed to update apn. Code: ${err.code}, message: ${err.message}`);
}

```

