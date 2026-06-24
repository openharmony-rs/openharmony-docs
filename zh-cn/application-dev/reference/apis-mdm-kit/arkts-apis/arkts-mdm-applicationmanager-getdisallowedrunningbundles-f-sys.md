# getDisallowedRunningBundles（系统接口）

## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, callback: AsyncCallback<Array<string>>): void
```

��ȡ��ǰ�û��µ�Ӧ�����н�ֹ������ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | �ص�����������ȡӦ�����н�ֹ�����ɹ�ʱ��errΪnull������Ϊ�������<br/>**˵����** API version 20<br/>��֮ǰ�汾������ֵΪӦ��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�б�����API version 21�汾��ʼ������ֵΪ<br/>Ӧ��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
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

applicationManager.getDisallowedRunningBundles(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});

```


## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, userId: number, callback: AsyncCallback<Array<string>>): void
```

��ȡָ���û���ͨ��userIdָ�����µ�Ӧ�����н�ֹ������ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | �ص�����������ȡӦ�����н�ֹ�����ɹ�ʱ��errΪnull������Ϊ�������<br/>**˵����** API version 20<br/>��֮ǰ�汾������ֵΪӦ��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�б�����API version 21�汾��ʼ������ֵΪ<br/>Ӧ��[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
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

applicationManager.getDisallowedRunningBundles(wantTemp, 100, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});

```


## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, userId?: number): Promise<Array<string>>
```

��ȡ��ǰ/ָ���û��µ�Ӧ�����н�ֹ������ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getDisallowedRunningBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise���󣬷��ص�ǰ/ָ���û��µ�Ӧ�����н�ֹ������<br/>**˵����** API version 20��֮ǰ�汾������ֵΪӦ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�б�����API version 21�汾��ʼ������ֵΪӦ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

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

applicationManager.getDisallowedRunningBundles(wantTemp, 100).then((result) => {
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});

```

