# uninstall（系统接口）

## uninstall

```TypeScript
function uninstall(admin: Want, bundleName: string, callback: AsyncCallback<void>): void
```

ж�ص�ǰ�û��µ�ָ��Ӧ�ó�������Ҳ�����Ӧ�ó�������ݡ�ʹ��callback�첽�ص���

> **˵����**
>
> ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��
> [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)
> �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** uninstall(admin:

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ������ |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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

bundleManager.uninstall(wantTemp, 'bundleName', (err) => {
  if (err) {
    console.error(`Failed to uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in uninstalling bundles');
});

```


## uninstall

```TypeScript
function uninstall(admin: Want, bundleName: string, userId: number, callback: AsyncCallback<void>): void
```

ж��ָ���û��£��ɲ���userIdָ������ָ��Ӧ�ó�������Ҳ�����Ӧ�ó�������ݡ�ʹ��callback�첽�ص���

> **˵����**
>
> ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��
> [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)
> �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** uninstall(admin:

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ������ |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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

bundleManager.uninstall(wantTemp, 'bundleName', 100, (err) => {
  if (err) {
    console.error(`Failed to uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in uninstalling bundles');
});

```


## uninstall

```TypeScript
function uninstall(admin: Want, bundleName: string, isKeepData: boolean, callback: AsyncCallback<void>): void
```

ж�ص�ǰ�û��µ�ָ��Ӧ�ó������ѡ���Ƿ���Ӧ�ó�������ݣ���isKeepDataָ������ʹ��callback�첽�ص���

> **˵����**
>
> ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��
> [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)
> �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** uninstall(admin:

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ������ |
| isKeepData | boolean | 是 | �Ƿ��������ݣ�true��ʾ������false��ʾ�������� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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

bundleManager.uninstall(wantTemp, 'bundleName', true, (err) => {
  if (err) {
    console.error(`Failed to uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in uninstalling bundles');
});

```


## uninstall

```TypeScript
function uninstall(admin: Want, bundleName: string, userId: number, isKeepData: boolean, callback: AsyncCallback<void>): void
```

ж��ָ���û��£��ɲ���userIdָ������ָ��Ӧ�ó�����ӿڣ�ѡ���Ƿ���Ӧ�ó�������ݣ���isKeepDataָ������ʹ��callback�첽�ص���

> **˵����**
>
> ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��
> [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)
> �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** uninstall(admin:

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | ������ |
| userId | number | 是 | �û�ID��ָ�������û���ȡֵ��Χ�����ڵ���0�� |
| isKeepData | boolean | 是 | �Ƿ��������ݣ�true��ʾ������false��ʾ�������� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
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

bundleManager.uninstall(wantTemp, 'bundleName', 100, true, (err) => {
  if (err) {
    console.error(`Failed to uninstall bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in uninstalling bundles');
});

```

