# setDefaultData

## setDefaultData

```TypeScript
function setDefaultData(admin: Want, slotId: number): void
```

����ָ�����۵�SIM��ΪĬ���������������豸��ʹ��ָ�����۵�SIM�������������ýӿ���Ҫ����SIM�����رշ���ģʽ���ܳɹ����á�

**起始版本：** 26.0.0

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
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201020](../../errorcode-universal.md#9201020-Failed) | Failed to set the default data SIM card.<br/>The airplane mode is enabled or no SIM card is inserted. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-This) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let slotId: number = 0;
try {
  telephonyManager.setDefaultData(wantTemp, slotId);
  console.info(`success to set default data SIM ID`);
} catch (err) {
  console.error(`Failed to set default data. Code: ${err.code}, message: ${err.message}`);
}

```

