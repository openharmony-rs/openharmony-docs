# getAllowedInstallBundles（系统接口）

## getAllowedInstallBundles

```TypeScript
function getAllowedInstallBundles(admin: Want, callback: AsyncCallback<Array<string>>): void
```

获取当前用户下的应用程序包安装允许名单，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

bundleManager.getAllowedInstallBundles(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get allowed install bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting allowed install bundles, result : ${JSON.stringify(result)}`);
});

```


## getAllowedInstallBundles

```TypeScript
function getAllowedInstallBundles(admin: Want, userId: number, callback: AsyncCallback<Array<string>>): void
```

获取指定用户（通过userId指定）下的应用程序包安装允许名单，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| userId | number | 是 | 用户ID，指定具体用户。取值范围：大于等于0。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

bundleManager.getAllowedInstallBundles(wantTemp, 100, (err, result) => {
  if (err) {
    console.error(`Failed to get allowed install bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting allowed install bundles, result : ${JSON.stringify(result)}`);
});

```


## getAllowedInstallBundles

```TypeScript
function getAllowedInstallBundles(admin: Want, userId?: number): Promise<Array<string>>
```

获取当前/指定用户下的应用程序包安装允许名单，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [getAllowedInstallBundlesSync](arkts-mdm-getallowedinstallbundlessync-f.md#getallowedinstallbundlessync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| userId | number | 否 | 用户ID，取值范围：大于等于0。<br> - 调用接口时，若传入userId，表示指定用户。<br> - 调用接口时，若未传入userId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回当前/指定用户下的应用程序包安装允许名单。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

bundleManager.getAllowedInstallBundles(wantTemp, 100).then((result) => {
  console.info(`Succeeded in getting allowed install bundles, result : ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get allowed install bundles. Code is ${err.code}, message is ${err.message}`);
});

```

