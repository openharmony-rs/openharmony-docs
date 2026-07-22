# disableSuperAdmin（系统接口）

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## disableSuperAdmin

```TypeScript
function disableSuperAdmin(bundleName: String, callback: AsyncCallback<void>): void
```

根据bundleName将超级设备管理应用解除激活。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function disableSuperAdmin(bundleName: String, callback: AsyncCallback<void>): void--><!--Device-adminManager-function disableSuperAdmin(bundleName: String, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | 超级设备管理应用的包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当接口调用成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200005](../errorcode-enterpriseDeviceManager.md#9200005-解除激活设备管理器失败) | Failed to deactivate the administrator application of the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.disableSuperAdmin(bundleName, (err) => {
  if (err) {
    console.error(`Failed to disable super admin. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in disabling super admin');
});

```


## disableSuperAdmin

```TypeScript
function disableSuperAdmin(bundleName: String): Promise<void>
```

根据bundleName将超级设备管理应用解除激活。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function disableSuperAdmin(bundleName: String): Promise<void>--><!--Device-adminManager-function disableSuperAdmin(bundleName: String): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | 超级设备管理应用的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当解除激活超级设备管理应用失败时，会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200005](../errorcode-enterpriseDeviceManager.md#9200005-解除激活设备管理器失败) | Failed to deactivate the administrator application of the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.disableSuperAdmin(bundleName).catch((err: BusinessError) => {
  console.error(`Failed to disable super admin. Code: ${err.code}, message: ${err.message}`);
});

```

