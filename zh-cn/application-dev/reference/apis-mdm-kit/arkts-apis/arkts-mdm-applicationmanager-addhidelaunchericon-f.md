# addHideLauncherIcon

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="addhidelaunchericon"></a>
## addHideLauncherIcon

```TypeScript
function addHideLauncherIcon(admin: Want, bundleNames: Array<string>): void
```

添加隐藏桌面应用图标名单。

> **说明：**  
>  
> 1、本接口仅支持隐藏当前用户的桌面应用图标，不支持隐藏应用卡片。  
>  
> 2、如果被隐藏的应用有应用分身，会同步隐藏应用分身。  
>  
> 3、不能把桌面所有应用都添加到隐藏名单中，否则所有应用都会显示到桌面上。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addHideLauncherIcon(admin: Want, bundleNames: Array<string>): void--><!--Device-applicationManager-function addHideLauncherIcon(admin: Want, bundleNames: Array<string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定需要隐藏的应用，最大支持500个。 |

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
  applicationManager.addHideLauncherIcon(wantTemp, bundleNames);
  console.info('Succeeded in adding hide launcher icon.');
} catch (err) {
  console.error(`Failed to add hide launcher icon. Code is ${err.code}, message is ${err.message}`);
}

```

