# setUserRestriction

## setUserRestriction

```TypeScript
function setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void
```

�����û���Ϊ�����ƹ���

**起始版本：** 20

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| settingsItem | string | 是 | ��Ϊ���ơ�<br/>- setApn��APN���ã���ǰ��֧���ֻ���ƽ��ʹ�á�<br/>- powerLongPress��������Դ���򿪵�Դ�˵�����ǰ��֧���ֻ���ƽ��<br/>ʹ�á�<br/>- setEthernetIp���޸���̫��IP��ַ����ǰ��֧��PC/2in1�豸ʹ�á�<br/>- setDeviceName���޸��豸���ƣ���ǰ��֧��PC/2in1�豸���ֻ���ƽ��ʹ�á����ú�PC/2<br/>in1�豸�������������豸�����޷��޸ģ��������ڱ��������������豸Эͬ-&gt;�������ֻ���ƽ���豸�����еĹ��ڱ����������������ȵ���豸�����޷��޸ġ�<br/>- setBiometricsAndScreenLock���޸�����<br/>���룬��ǰ��֧��PC/2in1�豸���ֻ���ƽ��ʹ�á� |
| restricted | boolean | 是 | �Ƿ������Ϊ��true��ʾ���ã�false��ʾ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  restrictions.setUserRestriction(wantTemp, 'setApn', true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}

```

