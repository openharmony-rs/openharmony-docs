# removeUserNonStopApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## removeUserNonStopApps

```TypeScript
function removeUserNonStopApps(admin: Want, applicationInstances: Array<common.ApplicationInstance>): void
```

为指定用户删除不可关停应用名单。执行删除策略时，若参数列表中包含未安装应用，删除操作仍能成功执行；已安装的应用将被删除，未安装的应用不影响删除操作。

**起始版本：** 22

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function removeUserNonStopApps(admin: Want, applicationInstances: Array<common.ApplicationInstance>): void--><!--Device-applicationManager-function removeUserNonStopApps(admin: Want, applicationInstances: Array<common.ApplicationInstance>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| applicationInstances | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<common.ApplicationInstance> | 是 | 不可关停应用名单数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // 需根据实际情况进行替换
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.removeUserNonStopApps(wantTemp, applicationInstances);
  console.info('Succeeded in removing UserNonStop applications.');
} catch(err) {
  console.error(`Failed to remove UserNonStop applications. Code: ${err.code}, message: ${err.message}`);
}

```

