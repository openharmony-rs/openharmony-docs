# addOutgoingCallPolicyNumbers

## addOutgoingCallPolicyNumbers

```TypeScript
function addOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array<string>): void
```

����ͨ��������������������������������������������붼���Ժ��������Ӻ�ֻ�������ڵĺ����������ֹ������

��������£�ͨ�����ӿ�����ͨ������������������������ᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ������豸ͨ����������ͨ�����ӿ�����ͨ�������Ľ��û���������������203�����롣ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�������豸ͨ�������󣬿ɽ����ͻ��
2. �Ѿ�ͨ�����ӿ�������ͨ�������Ľ�����������ͨ�����ӿ�����ͨ��������������������9200010�����롣ͨ��[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeOutgoingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ���������������Ƴ��󣬿ɽ����ͻ��
3. �Ѿ�ͨ�����ӿ�������ͨ��������������������ͨ�����ӿ�����ͨ��������������������9200010�����롣ͨ��[removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md#removeOutgoingCallPolicyNumbers-1)�ӿڽ�֮ǰ���õ�ͨ���������������Ƴ��󣬿ɽ����ͻ��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| policy | adminManager.Policy | 是 | ����������������ԡ�BLOCK_LISTΪ����������TRUST_LISTΪ���������� |
| numbers | Array&lt;string&gt; | 是 | ͨ�������б�����ǰ��֧��ȫ����ƥ�䡣�����ܳ��Ȳ��ܳ���1000�����磬����ǰ������������������100�����룬�����֧��ͨ���ýӿ�������900���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-This) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';
import { adminManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  telephonyManager.addOutgoingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in adding outgoing call policy.');
} catch (err) {
  console.error(`Failed to add outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}

```

