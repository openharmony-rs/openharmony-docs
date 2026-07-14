# removeHideLauncherIcon

## removeHideLauncherIcon

```TypeScript
function removeHideLauncherIcon(admin: Want, bundleNames: Array<string>): void
```

取消隐藏桌面应用图标名单。

> **说明：**
>
> 取消隐藏的应用会从桌面第2屏开始找空位显示；如果第2~18屏无空位，则在第1屏找空位；如果第1屏无空位，则在第2屏第1个应用的位置创建小文件夹放置应用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定需要取消隐藏的应用，最大支持500个。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
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
// 需根据实际情况进行替换
let bundleNames: Array<string> = ['com.example.test'];
try {
  applicationManager.removeHideLauncherIcon(wantTemp, bundleNames);
  console.info('Succeeded in removing hide launcher icon.');
} catch (err) {
  console.error(`Failed to remove hide launcher icon. Code is ${err.code}, message is ${err.message}`);
}

```

