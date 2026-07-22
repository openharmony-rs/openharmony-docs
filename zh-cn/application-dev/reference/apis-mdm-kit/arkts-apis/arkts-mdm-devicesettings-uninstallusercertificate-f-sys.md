# uninstallUserCertificate（系统接口）

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## uninstallUserCertificate

```TypeScript
function uninstallUserCertificate(admin: Want, certUri: string, callback: AsyncCallback<void>): void
```

卸载用户证书，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallusercertificate)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function uninstallUserCertificate(admin: Want, certUri: string, callback: AsyncCallback<void>): void--><!--Device-deviceSettings-function uninstallUserCertificate(admin: Want, certUri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| certUri | string | 是 | 证书uri，由安装用户证书接口[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installusercertificate)设置返回。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201001](../errorcode-enterpriseDeviceManager.md#9201001-管理证书失败) | Failed to manage the certificate. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

卸载用户证书，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallusercertificate)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function uninstallUserCertificate(admin: Want, certUri: string): Promise<void>--><!--Device-deviceSettings-function uninstallUserCertificate(admin: Want, certUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| certUri | string | 是 | 证书uri，由安装用户证书接口[installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md#installusercertificate)设置返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当卸载用户证书失败时会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201001](../errorcode-enterpriseDeviceManager.md#9201001-管理证书失败) | Failed to manage the certificate. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

