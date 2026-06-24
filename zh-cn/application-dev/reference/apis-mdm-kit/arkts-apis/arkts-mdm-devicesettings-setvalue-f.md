# setValue

## setValue

```TypeScript
function setValue(admin: Want, item: string, value: string): void
```

�����豸���ԡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| item | string | 是 | �豸���ò������͡�<br/>- screenOff���豸Ϣ�����ԡ�����PC/2in1�豸��֧�����õ�غ͵�Դ�����µ��豸Ϣ�����ԡ�<br/>- dateTime������ϵͳʱ�䡣- powerPolicy���豸��Դ���ԡ���������֧��PC/2in1�豸����������֮��ˢ�����á���Դ�͵��ҳ�棬���ֻ�ƽ���豸���ú���Ч��<br/>����PC/2in1�豸����֧�����õ�ع����µ��豸��Դ���ԡ���<br/>���豸��ʱ����ʱ˯���ӳٲ��ԣ�˯�߶�����Ҫ�����á���Դ�͵��ҳ����ʾ��˯��ʱ��֮��ȴ����õ�delayTime�Ż���Ч��<br/>- eyeComfort����API version 23��ʼ֧�֣����û���ģʽ����״̬����֧<br/>��ȫ�쿪���͹رջ���ģʽ��<br/>- defaultInputMethod����API version 23��ʼ֧�֣�����Ĭ�����뷨�� |
| value | string | 是 | �豸���ò������͡�<br/>- screenOff���豸Ϣ�����ԡ�����PC/2in1�豸��֧�����õ�غ͵�Դ�����µ��豸Ϣ�����ԡ�<br/>- dateTime������ϵͳʱ�䡣- powerPolicy���豸��Դ���ԡ���������֧��PC/2in1�豸����������֮��ˢ�����á���Դ�͵��ҳ�棬���ֻ�ƽ���豸���ú���Ч��<br/>����PC/2in1�豸����֧�����õ�ع����µ��豸��Դ���ԡ���<br/>���豸��ʱ����ʱ˯���ӳٲ��ԣ�˯�߶�����Ҫ�����á���Դ�͵��ҳ����ʾ��˯��ʱ��֮��ȴ����õ�delayTime�Ż���Ч��<br/>- eyeComfort����API version 23��ʼ֧�֣����û���ģʽ����״̬����֧<br/>��ȫ�쿪���͹رջ���ģʽ��<br/>- defaultInputMethod����API version 23��ʼ֧�֣�����Ĭ�����뷨�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  deviceSettings.setValue(wantTemp, 'screenOff', '3000');
  console.info(`Succeeded in setting screen off time.`);
} catch (err) {
  console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}

```

