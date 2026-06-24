# addKeepAliveApps

## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number): void
```

���ӱ���Ӧ�����������Ӻ��Զ�����Ӧ�ý��̡��ڿ�����Ӧ�ñ�ɱ������ϵͳ��������Ӧ�ý��̡�<!--RP7--><!--RP7End-->

ͨ�����ӿ�����������������Ӧ�ã���ֹ�û����豸���ֶ�ȡ������<!--RP6--><!--RP6End-->������ͨ��
[removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md#removeKeepAliveApps-1)�ӿڽ�Ӧ�ôӱ����������Ƴ���

�����Ӧ��������Ӧ�ý�ֹ��������[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)���Ͳ��ܽ�Ӧ����
��������Ӧ������������ᱨ9200010��ͻ�����롣

�����Ҫ��Phone/Tablet�豸ʹ�����ƹ��ܣ����Ե���[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)����
[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)�ӿڣ����幦����ο�����ĵ���

**起始版本：** 14

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleNames | Array&lt;string&gt; | 是 | Ӧ�ð������飬ָ����Ҫ����������������Ӧ�ã����֧��5���� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9201005](../../errorcode-universal.md#9201005-Add) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.The application does not have the permission<br/>required to call the API |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.Incorrect parameter types;3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding keep alive apps.');
} catch (err) {
  console.error(`Failed to add keep alive apps. Code is ${err.code}, message is ${err.message}`);
}

```


## addKeepAliveApps

```TypeScript
function addKeepAliveApps(admin: Want, bundleNames: Array<string>, accountId: number, disallowModify: boolean): void
```

���ӱ���Ӧ���������������Ƿ��ֹ�û��ֶ�ȡ��������Ӻ��Զ�����Ӧ�ý��̡��ڿ�����Ӧ�ñ�ɱ������ϵͳ��������Ӧ�ý��̡�

ͨ�����ӿڡ�
[addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md#addKeepAliveApps-1)
�ӿھ������ӱ���Ӧ�������������ӿڵ����ÿ�ͬʱ��Ч��ͬһ�û��£�����Ӧ���������֧�ְ���5��Ӧ�á����磺����ǰ����������3��Ӧ�ã�����໹��ͨ�����ӿ�Ϊ��ǰ�û�����2��Ӧ�á�

���ͨ��[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)�ӿڽ�Ӧ��������Ӧ�ý�ֹ�����������Ͳ���
��Ӧ������������Ӧ������������ᱨ9200010��ͻ�����롣

�����Ҫ��Phone/Tablet�豸ʹ�����ƹ��ܣ����Ե���[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)����
[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)�ӿڣ����幦����ο�����ĵ���

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleNames | Array&lt;string&gt; | 是 | Ӧ�ð������飬ָ����Ҫ����������������Ӧ�ã����֧��5����<br/>Ӧ����Ҫ������������װ��1�û��£�1�û���֧������Ӧ�õ������е��û�������Ӧ�ý���<br/>[��̨����](../../../../application-models/app-service-extension-ability.md#ʵ��һ����̨����)�����򣬻ᱨ������9<br/>201005�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| disallowModify | boolean | 是 | �Ƿ��ֹ�û��ֶ�ȡ��Ӧ�ñ��true��ʾ��ֹ��false��ʾ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9201005](../../errorcode-universal.md#9201005-Add) | Add keep alive applications failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.The application does not have the permission<br/>required to call the API |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况进行替换
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100, true);
  console.info('Succeeded in adding keep alive apps and set disallowModify.');
} catch (err) {
  console.error(`Failed to add keep alive apps and set disallowModify. Code is ${err.code}, message is ${err.message}`);
}

```

