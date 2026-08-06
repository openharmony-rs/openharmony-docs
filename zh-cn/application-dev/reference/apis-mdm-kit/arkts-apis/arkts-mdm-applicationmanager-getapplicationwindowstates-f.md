# getApplicationWindowStates

## getApplicationWindowStates

```TypeScript
function getApplicationWindowStates(admin: Want, bundleName: string, appIndex: number): Array<WindowStateInfo>
```

查询指定应用的窗口状态信息列表。可以查询到应用是否在底部Dock栏，以及当前应用窗口是否在前台显示等信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getApplicationWindowStates(admin: Want, bundleName: string, appIndex: number): Array<WindowStateInfo>--><!--Device-applicationManager-function getApplicationWindowStates(admin: Want, bundleName: string, appIndex: number): Array<WindowStateInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleName | string | 是 | 应用的包名。 |
| appIndex | number | 是 | 应用分身索引，取值范围：大于等于0的整数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ appIndex可以通过@ohos.bundle.bundleManager中的[getAppCloneIdentity]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WindowStateInfo&gt; | 返回应用窗口状态信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 被查询的应用包名，需根据实际情况进行替换
let bundleName: string = 'com.example.myapplication';
// 被查询应用的分身索引，需根据实际情况进行替换
let appIndex: number = 0;
try {
  let result: Array<applicationManager.WindowStateInfo> = applicationManager.getApplicationWindowStates(wantTemp, bundleName, appIndex);
  console.info(`Succeeded in getting application window states, result: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get application window states. Code: ${err.code}, message: ${err.message}`);
}
```

