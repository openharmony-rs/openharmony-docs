# removeDisallowedBluetoothProtocols

## removeDisallowedBluetoothProtocols

```TypeScript
function removeDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>): void
```

�Ƴ�����Э��������������Ƴ�����������ĳ���û��Ĳ�������Э�飬����û�����ʹ�ý���������ʣ�������Э���������豸�ⷢ�ļ������Ƴ�����������ĳ���û�����������Э�飬����û�����ʹ����������Э���������豸�ⷢ�ļ������Ƴ����������в���
�ڵ�����Э�飬�ӿڿɵ��óɹ����������Ƴ����������в����ڵ�����Э�顣

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| protocols | Array&lt;Protocol&gt; | 是 | ����Э������顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let accountId: number = 100;
let protocols: Array<bluetoothManager.Protocol> = [bluetoothManager.Protocol.GATT, bluetoothManager.Protocol.SPP];
try {
  bluetoothManager.removeDisallowedBluetoothProtocols(wantTemp, accountId, protocols);
  console.info('Succeeded in removing disallowed bluetooth protocols policy.');
} catch (err) {
  console.error(`Failed to remove disallowed bluetooth protocols. Code: ${err.code}, message: ${err.message}`);
}

```


## removeDisallowedBluetoothProtocols

```TypeScript
function removeDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>, policy: TransferPolicy): void
```

�ӽ����������Ƴ�����Э�顣�Ƴ���ָ���û��������ܸô�����Ե����ƣ���������ʹ����Щ����Э�顣

> **˵����**
>

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| protocols | Array&lt;Protocol&gt; | 是 | ����Э�����飬ָ����Ҫ�ӽ����������Ƴ���Э�顣 |
| policy | TransferPolicy | 是 | ������ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let accountId: number = 100;
let protocols: Array<bluetoothManager.Protocol> = [
  bluetoothManager.Protocol.GATT,
  bluetoothManager.Protocol.SPP,
  bluetoothManager.Protocol.OPP
];

try {
  bluetoothManager.removeDisallowedBluetoothProtocols(wantTemp, accountId, protocols, bluetoothManager.TransferPolicy.RECEIVE_SEND);
  console.info('Succeeded in removing disallowed bluetooth protocols.');
} catch (err) {
  console.error(`Failed to remove disallowed bluetooth protocols. Code is ${err.code}, message is ${err.message}`);
}

```

