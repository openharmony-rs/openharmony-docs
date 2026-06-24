# removeDisallowedUninstallBundles（系统接口）

## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void
```

�Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ�û���ж�أ�ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removeDisallowedUninstallBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���顣<br/>**˵����** ��API version 21�汾��ʼ�������е�Ԫ��֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�����Ƴ������<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���������Ƴ�ͬһӦ�õ�<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����API version 20��֮ǰ�汾�������е�Ԫ��ֻ֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed uninstall bundles');
});

```


## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void
```

�Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò�������ָ���û���ͨ��userIdָ������ж�ء�ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removeDisallowedUninstallBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���顣<br/>**˵����** ��API version 21�汾��ʼ�������е�Ԫ��֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�����Ƴ������<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���������Ƴ�ͬһӦ�õ�<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����API version 20��֮ǰ�汾�������е�Ԫ��ֻ֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
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

**示例：**

```TypeScript
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed uninstall bundles');
});

```


## removeDisallowedUninstallBundles

```TypeScript
function removeDisallowedUninstallBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>
```

�Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�á��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removeDisallowedUninstallBundlesSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| appIds | Array&lt;string&gt; | 是 | Ӧ��ID���顣<br/>**˵����** ��API version 21�汾��ʼ�������е�Ԫ��֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)��<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)�����Ƴ������<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)���������Ƴ�ͬһӦ�õ�<br/>[appIdentifier](../../../../quick-start/common-problem-of-application.md#ʲô��appidentifier)����<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)����API version 20��֮ǰ�汾�������е�Ԫ��ֻ֧��ʹ��<br/>[appId](../../../../quick-start/common-problem-of-application.md#ʲô��appid)�� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵��Ƴ�Ӧ�ó����ж�ؽ�ֹ����ʧ��ʱ���׳�������� |

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

bundleManager.removeDisallowedUninstallBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in removing disallowed uninstall bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
});

```

