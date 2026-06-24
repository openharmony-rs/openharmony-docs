# operateDevice

## operateDevice

```TypeScript
function operateDevice(admin: Want, operate: string, addition?: string): void
```

��������Ա�����豸��

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_OPERATE_DEVICE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| operate | string | 是 | Ҫִ�еĲ�����<br/>- resetFactory���豸�ָ��������á��ӿڵ��ú��豸�������ָ��������á��ָ���ɺ������豸���ݽ�ȫ�����������޷��ָ�����ҵ��Ҫ����Ӧ�õ�<br/>��ȫ��ƣ���ֹӦ�ñ�����������ҵ���ݶ�ʧ��<br/>- reboot���豸������<br/>- shutDown���豸�ػ���<br/>- lockScreen���豸������ |
| addition | string | 否 | ִ��ʱ���Ӳ�����Ŀǰ���贫�롣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceControl } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  deviceControl.operateDevice(wantTemp, 'resetFactory');
} catch (err) {
  console.error(`Failed to reset factory. Code is ${err.code}, message is ${err.message}`);
}

```

