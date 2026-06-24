# getOutgoingCallPolicyNumbers

## getOutgoingCallPolicyNumbers

```TypeScript
function getOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array<string>
```

��ȡͨ�����������������������

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| policy | adminManager.Policy | 是 | ����������������ԡ� BLOCK_LISTΪ����������TRUST_LISTΪ���������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ͨ���������û����������ĺ������顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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
  let numbers: Array<string> = telephonyManager.getOutgoingCallPolicyNumbers(wantTemp, policy);
  console.info(`Succeeded in getting outgoing call policy. result: ${JSON.stringify(numbers)}`);
} catch (err) {
  console.error(`Failed to get outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}

```

