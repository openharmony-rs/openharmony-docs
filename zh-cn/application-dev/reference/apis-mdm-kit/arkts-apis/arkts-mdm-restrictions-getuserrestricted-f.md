# getUserRestricted

## getUserRestricted

```TypeScript
function getUserRestricted(admin: Want, settingsItem: string): boolean
```

��ȡ������Ľ���״̬��

**起始版本：** 20

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| settingsItem | string | 是 | ָ�������<br/>- setEthernetIp���޸���̫��IP��ַ����ǰ��֧��PC/2in1�豸ʹ�á�<br/>- setDeviceName���޸��豸���ƣ�<br/>��ǰ��֧��PC/2in1�豸���ֻ���ƽ��ʹ�á�PC/2in1�豸�����й��ڱ��������������豸Эͬ-&gt;�����е��豸���ơ��ֻ���ƽ���豸�����й��ڱ����������������ȵ���豸���ơ�<br/>-<br/>setBiometricsAndScreenLock���޸��������룬��ǰ��֧��PC/2in1�豸���ֻ���ƽ��ʹ�á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����ָ��������Ľ���״̬��true��ʾ�ѽ��ã�false��ʾδ���á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 入参需根据实际情况替换
  let result: boolean = restrictions.getUserRestricted(wantTemp, 'setEthernetIp');
  console.info('Succeeded in getting user restricted');
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}

```

