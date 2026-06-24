# uninstallUserCertificate（系统接口）

## uninstallUserCertificate

```TypeScript
function uninstallUserCertificate(admin: Want, certUri: string, callback: AsyncCallback<void>): void
```

ж���û�֤�飬ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallUserCertificate-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| certUri | string | 是 | ֤��uri���ɰ�װ�û�֤��ӿ�<br/>[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installUserCertificate-1)<br/>���÷��ء� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201001](../../errorcode-universal.md#9201001-Failed) | Failed to manage the certificate. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
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
// 需根据实际情况进行替换
let aliasStr = "certName";
deviceSettings.uninstallUserCertificate(wantTemp, aliasStr, (err) => {
  if (err) {
    console.error(`Failed to uninstall user certificate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in uninstalling user certificate`);
});

```


## uninstallUserCertificate

```TypeScript
function uninstallUserCertificate(admin: Want, certUri: string): Promise<void>
```

ж���û�֤�飬ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallUserCertificate-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| certUri | string | 是 | ֤��uri���ɰ�װ�û�֤��ӿ�<br/>[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installUserCertificate-2)���÷��ء� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�ж���û�֤��ʧ��ʱ���׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201001](../../errorcode-universal.md#9201001-Failed) | Failed to manage the certificate. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let aliasStr = "certName"
deviceSettings.uninstallUserCertificate(wantTemp, aliasStr).then(() => {
  console.info(`Succeeded in uninstalling user certificate`);
}).catch((err: BusinessError) => {
  console.error(`Failed to uninstall user certificate. Code is ${err.code}, message is ${err.message}`);
});

```

