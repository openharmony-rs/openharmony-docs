# addDisallowedRunningBundles（系统接口）

## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void
```

����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ�û������У����ڽ�ֹ�����е�Ӧ���������С�ʹ��callback�첽�ص�����API version 21��ʼ�����Ӧ��������������
[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�
���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���飬ָ������Ӧ�á�<br/>**˵����** ��API version 21�汾��ʼ��֧�ִ���Ӧ�õ�<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���Ƽ�ʹ��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)��API version 20��֮ǰ�汾����֧<br/>��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured.&lt;br&gt;**适用版本：** 21+ |

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
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});

```


## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void
```

����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò�������ָ���û���ͨ��userIdָ���������У����ڽ�ֹ�����е�Ӧ���������С�ʹ��callback�첽�ص�����API version 21��ʼ�����Ӧ��������������
[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�
���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���飬ָ������Ӧ�á�<br/>**˵����** ��API version 21�汾��ʼ��֧�ִ���Ӧ�õ�<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���Ƽ�ʹ��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)��API version 20��֮ǰ�汾����֧<br/>��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured.&lt;br&gt;**适用版本：** 21+ |

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
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});

```


## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>
```

����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û������С�ʹ��Promise�첽�ص�����API version 21��ʼ�����Ӧ��������������
[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�
���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���飬ָ������Ӧ�á�<br/>**˵����** ��API version 21�汾��ʼ��֧�ִ���Ӧ�õ�<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���Ƽ�ʹ��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)��API version 20��֮ǰ�汾����֧<br/>��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�����Ӧ�����н�ֹ����ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured.&lt;br&gt;**适用版本：** 21+ |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in adding disallowed running bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});

```

