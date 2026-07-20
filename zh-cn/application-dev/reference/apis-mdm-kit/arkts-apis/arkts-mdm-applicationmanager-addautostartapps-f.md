# addAutoStartApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="addautostartapps"></a>
## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>): void
```

为当前用户添加开机自启动应用名单。通过本接口添加至自启动名单的应用，禁止用户在设备上手动取消应用自启动<!--RP4--><!--RP4End-->，但可通过[removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeautostartapps-1)接口将应用从自启动名单中移除。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addAutoStartApps(admin: Want, autoStartApps: Array<Want>): void--><!--Device-applicationManager-function addAutoStartApps(admin: Want, autoStartApps: Array<Want>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| autoStartApps | Array&lt;Want&gt; | 是 | 开机自启动应用数组。数组长度上限为10。例如：如果名单中已有5个应用，则最多再通过本接口设置5个。Want中必须包含bundleName和abilityName。Ability支持UIAbility和ServiceExtensionAbility。当[abilities](docroot://quick-start/module-configuration-file.md#abilities标签)标签中exported属性值为false时，不支持拉起Ability。从API version 24开始，新增支持通过Want的parameters属性中的isHiddenStart字段配置应用开机自启是否隐藏UI界面，true表示隐藏，false表示不隐藏。默认值是false。该参数设置为true时，应用必须<!--RP8-->接入状态栏<!--RP8End-->，否则自启设置失败（若当前仅设置一个应用自启时隐藏UI界面，该应用未接入状态栏，则抛出401异常；若设置多个应用，有一个设置成功，返回成功）。设置成功后，应用自启后不显示UI界面，仅在状态栏显示，UI进程存在。隐藏UI界面能力仅在PC/2in1和Tablet的PC模式中可正常使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let autoStartApps: Array<Want> = [
  {
    // 需根据实际情况进行替换
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // 下面为非必选参数
    parameters: {
      // 从API version 24开始支持，配置应用开机自启时，是否隐藏UI界面，true代表隐藏，该参数设置为true时，应用需接入状态栏，否则自启设置失败，抛出401异常。
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps);
  console.info('Succeeded in adding auto start applications.');
} catch(err) {
  console.error(`Failed to add auto start applications. Code: ${err.code}, message: ${err.message}`);
}

```


<a id="addautostartapps-1"></a>
## addAutoStartApps

```TypeScript
function addAutoStartApps(admin: Want, autoStartApps: Array<Want>, accountId: number, disallowModify: boolean): void
```

为指定用户添加开机自启动应用名单，并设置是否禁止该用户手动取消应用自启动<!--RP4--><!--RP4End-->。

通过本接口、[addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addautostartapps-1)接口均可添加开机自启动应用名单，两个接口的设置可同时生效。同一用户下，开机自启动应用名单最多支持包含10个应用。例如：若当前名单中已有3个应用，则最多还能通过本接口为当前用户添加7个应用。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addAutoStartApps(admin: Want, autoStartApps: Array<Want>, accountId: number, disallowModify: boolean): void--><!--Device-applicationManager-function addAutoStartApps(admin: Want, autoStartApps: Array<Want>, accountId: number, disallowModify: boolean): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| autoStartApps | Array&lt;Want&gt; | 是 | 开机自启动应用名单数组，数组总长度不超过10。Want中必须包含bundleName和abilityName。Ability支持UIAbility和ServiceExtensionAbility。当[abilities](docroot://quick-start/module-configuration-file.md#abilities标签)标签中exported属性值为false时，不支持拉起Ability。从API version 24开始，新增支持通过Want的parameters属性中的isHiddenStart字段配置应用开机自启是否隐藏UI界面，true表示隐藏，false表示不隐藏。默认值是false。该参数设置为true时，应用必须<!--RP8-->接入状态栏<!--RP8End-->，否则自启设置失败（若当前仅设置一个应用自启时隐藏UI界面，该应用未接入状态栏，则抛出401异常；若设置多个应用，有一个设置成功，返回成功）。设置成功后，应用自启后不显示UI界面，仅在状态栏显示，UI进程存在。隐藏UI界面能力仅在PC/2in1和Tablet的PC模式中可正常使用。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |
| disallowModify | boolean | 是 | 是否禁止用户手动取消应用自启动，true表示禁止，false表示允许。<!--RP1--><!--RP1End--> |

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

let autoStartApps: Array<Want> = [
  // 需根据实际情况进行替换
  {
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EntryAbility',
    // 下面为非必选参数
    parameters: {
      // 从API version 24开始支持，配置应用开机自启时，是否隐藏UI界面，true代表隐藏，该参数设置为true时，应用需接入状态栏，否则自启设置失败，抛出401异常。
      isHiddenStart: true 
    }
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps, 100, true);
  console.info('Succeeded in adding auto start applications and set disallowModify.');
} catch(err) {
  console.error(`Failed to add auto start applications and set disallowModify. Code: ${err.code}, message: ${err.message}`);
}

```

