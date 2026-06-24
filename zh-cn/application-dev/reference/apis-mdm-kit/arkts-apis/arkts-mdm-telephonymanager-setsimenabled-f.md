# setSimEnabled

## setSimEnabled

```TypeScript
function setSimEnabled(admin: Want, slotId: number): void
```

���ָ�����۵�SIM�����á�ʹ��setSimDisabled����SIM��������setSimEnabled����SIM������Ҫ������-�ƶ�����-SIM�����������ֶ���SIM�����ء�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| slotId | number | 是 | ����ID��Ŀǰ��֧�ֵ������豸��˫�����豸��ȡֵ��ΧΪ0��1������0��ʾ����1��1��ʾ����2�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let slotId: number = 0;
  telephonyManager.setSimEnabled(wantTemp, slotId);
  console.info(`Succeeded in setting slotId: ${slotId} enabled.`);
} catch (err) {
  console.error(`Failed to set slotId enabled. Code: ${err.code}, message: ${err.message}`);
}

```

