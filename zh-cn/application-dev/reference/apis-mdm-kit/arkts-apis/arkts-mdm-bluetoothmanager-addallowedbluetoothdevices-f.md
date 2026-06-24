# addAllowedBluetoothDevices

## addAllowedBluetoothDevices

```TypeScript
function addAllowedBluetoothDevices(admin: Want, deviceIds: Array<string>): void
```

���������豸�������������������豸����������ǰ�豸���������Ӹ������µ������豸����API version 22��ʼ�������е�MAC��ַ�����������MAC�淶�����磺00:1A:2B:3C:4D:5E��������ʱ���Ƴ����Ϸ���MAC
��ַ�������ӺϷ���MAC��ַ��

��������£�ͨ�����ӿ����������豸�����������ᱨ���Գ�ͻ��

1. �Ѿ�ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿڽ�����������ͨ��[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)�ӿ����������󣬿ɽ����ͻ��
2. �Ѿ�ͨ��[addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md#addDisallowedBluetoothDevices-1)�ӿ������������豸����������ͨ��[removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md#removeDisallowedBluetoothDevices-1)�Ƴ������豸���������󣬿ɽ����ͻ��

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| deviceIds | Array&lt;string&gt; | 是 | �����豸MAC��ַ�����顣�����豸�����������鳤������Ϊ1000������ǰ��������������300�������豸MAC��ַ����ֻ����������700���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let deviceIds: Array<string> = ["00:1A:2B:3C:4D:5E","AA:BB:CC:DD:EE:FF"];
try {
  bluetoothManager.addAllowedBluetoothDevices(wantTemp,deviceIds);
  console.info(`Succeeded in adding allowed bluetooth devices.`);
} catch(err) {
  console.error(`Failed to add allowed bluetooth devices. Code: ${err.code}, message: ${err.message}`);
}

```

