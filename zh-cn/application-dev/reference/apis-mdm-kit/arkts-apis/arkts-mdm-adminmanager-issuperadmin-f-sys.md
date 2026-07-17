# isSuperAdmin（系统接口）

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## isSuperAdmin

```TypeScript
function isSuperAdmin(bundleName: String, callback: AsyncCallback<boolean>): void
```

根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function isSuperAdmin(bundleName: String, callback: AsyncCallback<boolean>): void--><!--Device-adminManager-function isSuperAdmin(bundleName: String, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | 超级设备管理应用。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数，当接口调用成功，err为null，data为boolean类型值，true表示当前用户下指定的设备管理应用被激活，false表示当前用户下指定的设备管理应用未激活，否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.isSuperAdmin(bundleName, (err, result) => {
  if (err) {
    console.error(`Failed to query admin is super admin or not. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying admin is super admin or not, result : ${result}`);
});

```


## isSuperAdmin

```TypeScript
function isSuperAdmin(bundleName: String): Promise<boolean>
```

根据bundleName查询首用户（u100）下的超级设备管理应用是否被激活。使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function isSuperAdmin(bundleName: String): Promise<boolean>--><!--Device-adminManager-function isSuperAdmin(bundleName: String): Promise<boolean>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | String | 是 | 超级设备管理应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象, 返回true表示指定的超级设备管理应用被激活，返回false表示指定的超级设备管理应用未激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';

adminManager.isSuperAdmin(bundleName).then((result) => {
  console.info(`Succeeded in querying admin is super admin or not, result : ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query admin is super admin or not. Code: ${err.code}, message: ${err.message}`);
});

```

