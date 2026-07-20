# isModifyAutoStartAppsDisallowed

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="ismodifyautostartappsdisallowed"></a>
## isModifyAutoStartAppsDisallowed

```TypeScript
function isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean
```

查询指定用户是否禁止取消应用自启动。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean--><!--Device-applicationManager-function isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| autoStartApp | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 开机自启动应用。Want中必须包含bundleName和abilityName。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否禁止用户取消应用自启动，true表示禁止，false表示允许。<!--PR1--><!--PR1End--> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
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

let autoStartApp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.autoStartApplication',
  abilityName: 'EntryAbility'
};

try {
  let res: boolean = applicationManager.isModifyAutoStartAppsDisallowed(wantTemp, autoStartApp, 100);
  console.info(`Succeeded in getting disallow modify auto start app: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get disallow modify auto start app. Code: ${err.code}, message: ${err.message}`);
}

```

