# installUserCertificate（系统接口）

## installUserCertificate

```TypeScript
function installUserCertificate(admin: Want, certificate: CertBlob, callback: AsyncCallback<string>): void
```

��װ�û�֤�飬ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installUserCertificate-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| certificate | CertBlob | 是 | ֤����Ϣ��֤���ļ�Ӧ����Ӧ��ɳ��·��(Ӧ��ɳ��·������ʵ·���Ķ�Ӧ��ϵ�ɲμ���<br/>[Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ](../../../../file-management/app-sandbox-directory.md#Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ))��Ӧ����Ȩ�޷��ʵ�·���¡� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

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
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let certFileArray: Uint8Array = new Uint8Array();
// 变量context需要在MainAbility的onCreate回调函数中进行初始化
// test.cer需要放置在rawfile目录下
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
context.resourceManager.getRawFileContent("test.cer").then((value) => {
  certFileArray = value;
  deviceSettings.installUserCertificate(wantTemp, { inData: certFileArray, alias: "cert_alias_xts" }, (err, result) => {
    if (err) {
      console.error(`Failed to install user certificate. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in installing user certificate, result : ${JSON.stringify(result)}`);
    }
  });
}).catch((error: BusinessError) => {
  console.error(`Failed to get raw file content. message: ${error.message}`);
  return;
});

```


## installUserCertificate

```TypeScript
function installUserCertificate(admin: Want, certificate: CertBlob): Promise<string>
```

��װ�û�֤�飬ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installUserCertificate-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| certificate | CertBlob | 是 | ֤����Ϣ��֤���ļ�Ӧ����Ӧ��ɳ��·��(Ӧ��ɳ��·������ʵ·���Ķ�Ӧ��ϵ�ɲμ���<br/>[Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ](../../../../file-management/app-sandbox-directory.md#Ӧ��ɳ��·������ʵ����·���Ķ�Ӧ��ϵ))��Ӧ����Ȩ�޷��ʵ�·���¡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬷��ص�ǰ֤�鰲װ���uri������ж��֤�顣 |

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
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let certFileArray: Uint8Array = new Uint8Array();
// 变量context需要在MainAbility的onCreate回调函数中进行初始化
// test.cer需要放置在rawfile目录下
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
context.resourceManager.getRawFileContent("test.cer").then((value) => {
  certFileArray = value
  deviceSettings.installUserCertificate(wantTemp, { inData: certFileArray, alias: "cert_alias_xts" })
    .then((result) => {
      console.info(`Succeeded in installing user certificate, result : ${JSON.stringify(result)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to install user certificate. Code: ${err.code}, message: ${err.message}`);
  })
}).catch((error: BusinessError) => {
  console.error(`Failed to get raw file content. message: ${error.message}`);
  return;
});

```

