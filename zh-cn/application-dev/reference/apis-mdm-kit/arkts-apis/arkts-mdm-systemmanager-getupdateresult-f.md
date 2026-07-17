# getUpdateResult

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getUpdateResult

```TypeScript
function getUpdateResult(admin: Want, version: string): Promise<UpdateResult>
```

获取系统更新结果。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function getUpdateResult(admin: Want, version: string): Promise<UpdateResult>--><!--Device-systemManager-function getUpdateResult(admin: Want, version: string): Promise<UpdateResult>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| version | string | 是 | 更新包版本号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<UpdateResult> | Promise对象，返回系统更新结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
systemManager.getUpdateResult(wantTemp, "1.0").then((result:systemManager.UpdateResult) => {
  console.info(`Succeeded in getting update result: ${JSON.stringify(result)}`);
}).catch((error: BusinessError) => {
  console.error(`Get update result failed. Code is ${error.code},message is ${error.message}`);
});

```

