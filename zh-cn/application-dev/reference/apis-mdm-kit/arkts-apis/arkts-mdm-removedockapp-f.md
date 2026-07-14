# removeDockApp

## removeDockApp

```TypeScript
function removeDockApp(admin: Want, bundleName: string, abilityName: string): void
```

从快捷栏中移除应用。

> **说明：**
>
> 以下应用不可通过本接口从快捷栏中移除：“应用中心”、“任务中心”、“文件管理”、“回收站”，否则报错9201018错误码。

> **说明**
> 以下应用不可通过本接口从快捷栏中移除：“应用中心”、“任务中心”、“文件管理”、“回收站”，否则报错9201018错误码。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用的包名。 |
| abilityName | string | 是 | 应用的Ability名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201016](../errorcode-enterpriseDeviceManager.md#9201016-指定应用不在快捷栏) | The application has not been added to the Dock. |
| [9201018](../errorcode-enterpriseDeviceManager.md#9201018-指定应用不支持操作) | The application is inoperable. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let bundleName: string = 'com.example.exampleapplication';
  let abilityName: string = 'EntryAbility';
  applicationManager.removeDockApp(wantTemp, bundleName, abilityName);
  console.info('Succeeded in removing dock app.');
} catch(err) {
  console.error(`Failed to remove dock app. Code: ${err.code}, message: ${err.message}`);
}

```

