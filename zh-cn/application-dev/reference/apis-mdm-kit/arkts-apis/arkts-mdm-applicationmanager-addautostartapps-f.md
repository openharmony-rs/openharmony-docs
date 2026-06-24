# addAutoStartApps

## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>): void
```

Ϊ��ǰ�û����ӿ���������Ӧ��������ͨ�����ӿ�������������������Ӧ�ã���ֹ�û����豸���ֶ�ȡ��Ӧ��������<!--RP4--><!--RP4End-->������ͨ��
[removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeAutoStartApps-1)�ӿڽ�Ӧ�ô���
�����������Ƴ���

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| autoStartApps | Array&lt;Want&gt; | 是 | ����������Ӧ�����顣���鳤������Ϊ10�����磺�������������5��Ӧ�ã��������ͨ�����ӿ�����5����Want�б������bundleName��<br/>abilityName��Ability֧��UIAbility��ServiceExtensionAbility����<br/>[abilities](../../../../quick-start/module-configuration-file.md#abilities��ǩ)��ǩ��exported����ֵΪfalseʱ����֧������Ability����<br/>API version 24��ʼ������֧��ͨ��Want��parameters�����е�isHiddenStart�ֶ�����Ӧ�ÿ��������Ƿ�����UI���棬true��ʾ���أ�false��ʾ�����ء�Ĭ��ֵ��false���ò�������Ϊ<br/>trueʱ��Ӧ�ñ�������״̬����������������ʧ�ܣ�����ǰ������һ��Ӧ������ʱ����UI���棬��Ӧ��δ����״̬�������׳�401�쳣�������ö��Ӧ�ã���һ�����óɹ������سɹ���������<br/>�ɹ���Ӧ����������ʾUI���棬����״̬����ʾ��UI���̴��ڡ�����UI������������PC/2in1��Tablet��PCģʽ�п�����ʹ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let autoStartApps: Array<Want> = [
  {
    // 需根据实际情况进行替换
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // 下面为非必选参数
    parameters: {
      // 从API version 24开始支持，配置应用开机自启时，是否隐藏UI界面，true代表隐藏，该参数设置为true时，应用需接入状态栏，否则自启设置失败，抛出401异常。
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps);
  console.info('Succeeded in adding auto start applications.');
} catch(err) {
  console.error(`Failed to add auto start applications. Code: ${err.code}, message: ${err.message}`);
}

```


## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>, accountId: number, disallowModify: boolean): void
```

Ϊָ���û����ӿ���������Ӧ���������������Ƿ��ֹ���û��ֶ�ȡ��Ӧ��������<!--RP4--><!--RP4End-->��

ͨ�����ӿڡ�[addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addAutoStartApps-1)�ӿھ������ӿ�
��������Ӧ�������������ӿڵ����ÿ�ͬʱ��Ч��ͬһ�û��£�����������Ӧ���������֧�ְ���10��Ӧ�á����磺����ǰ����������3��Ӧ�ã�����໹��ͨ�����ӿ�Ϊ��ǰ�û�����7��Ӧ�á�

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| autoStartApps | Array&lt;Want&gt; | 是 | ����������Ӧ���������飬�����ܳ��Ȳ�����10��Want�б������bundleName��abilityName��Ability֧��UIAbility��<br/>ServiceExtensionAbility����[abilities](../../../../quick-start/module-configuration-file.md#abilities��ǩ)��ǩ��exported<br/>����ֵΪfalseʱ����֧������Ability����API version 24��ʼ������֧��ͨ��Want��parameters�����е�isHiddenStart�ֶ�����Ӧ�ÿ��������Ƿ�����UI���棬true��ʾ���أ�<br/>false��ʾ�����ء�Ĭ��ֵ��false���ò�������Ϊtrueʱ��Ӧ�ñ�������״̬����������������ʧ�ܣ�����ǰ������һ��Ӧ������ʱ����UI���棬��Ӧ��δ����״̬�������׳�401<br/>�쳣�������ö��Ӧ�ã���һ�����óɹ������سɹ��������óɹ���Ӧ����������ʾUI���棬����״̬����ʾ��UI���̴��ڡ�����UI������������PC/2in1��Tablet��PCģʽ�п�����ʹ�á� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| disallowModify | boolean | 是 | �Ƿ��ֹ�û��ֶ�ȡ��Ӧ����������true��ʾ��ֹ��false��ʾ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let autoStartApps: Array<Want> = [
  // 需根据实际情况进行替换
  {
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // 下面为非必选参数
    parameters: {
      // 从API version 24开始支持，配置应用开机自启时，是否隐藏UI界面，true代表隐藏，该参数设置为true时，应用需接入状态栏，否则自启设置失败，抛出401异常。
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps, 100, true);
  console.info('Succeeded in adding auto start applications and set disallowModify.');
} catch(err) {
  console.error(`Failed to add auto start applications and set disallowModify. Code: ${err.code}, message: ${err.message}`);
}

```

