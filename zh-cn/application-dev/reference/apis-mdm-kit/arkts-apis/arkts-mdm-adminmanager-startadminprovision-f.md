# startAdminProvision

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

<a id="startadminprovision"></a>
## startAdminProvision

```TypeScript
function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record<string, string>): void
```

设备管理应用拉起BYOD管理员激活页面进行激活。

**起始版本：** 15

**需要权限：** ohos.permission.START_PROVISIONING_MESSAGE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record<string, string>): void--><!--Device-adminManager-function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record<string, string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| type | [AdminType](arkts-mdm-adminmanager-admintype-e.md) | 是 | 激活的设备管理应用类型，仅支持ADMIN_TYPE_BYOD类型。 |
| context | common.Context | 是 | 管理应用的上下文信息。 |
| parameters | Record&lt;string, string&gt; | 是 | 自定义参数信息，其中Key值必须包含："activateId"，可以包含"customizedInfo"、"localDeactivationPolicy"。<br/>- activateId：项目激活ID。<br/>- customizedInfo：企业自定义信息。<br/>- localDeactivationPolicy：从API version 22开始支持，本地延迟取消激活时间（单位：小时）<!--RP1--><!--RP1End-->。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let recordParameters: Record<string, string> = {
  // 需根据实际情况进行替换
  "activateId": "activateId testValue",
  "customizedInfo": "customizedInfo testValue"
};
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  console.info('context:' + JSON.stringify(context));
  adminManager.startAdminProvision(wantTemp, adminManager.AdminType.ADMIN_TYPE_BYOD, context, recordParameters);
  console.info('startAdminProvision::success');
} catch (error) {
  console.error('startAdminProvision::errorCode: ' + error.code + ' errorMessage: ' + error.message);
}

```

