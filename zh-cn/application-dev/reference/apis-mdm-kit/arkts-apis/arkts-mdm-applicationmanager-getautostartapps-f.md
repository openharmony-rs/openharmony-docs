# getAutoStartApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want): Array<Want>
```

查询当前用户开机自启动应用名单。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAutoStartApps(admin: Want): Array<Want>--><!--Device-applicationManager-function getAutoStartApps(admin: Want): Array<Want>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 应用自启动名单数组。从API version 24开始，支持返回是否隐藏UI的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp);
  console.info(`Succeeded in adding auto start apps: ${JSON.stringify(res)}`);
} catch (err) {
  console.error(`Failed to auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]
```


## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want | null): Array<Want>
```

查询当前用户开机自启动应用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAutoStartApps(admin: Want | null): Array<Want>--><!--Device-applicationManager-function getAutoStartApps(admin: Want | null): Array<Want>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 应用自启动名单数组。支持返回是否隐藏UI的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

try {
  // 参数需根据实际情况进行替换
  let res: Array<Want> = applicationManager.getAutoStartApps(null);
  console.info(`Succeeded in adding auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]
```


## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want, accountId: number): Array<Want>
```

查询指定用户下的开机自启动应用名单。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAutoStartApps(admin: Want, accountId: number): Array<Want>--><!--Device-applicationManager-function getAutoStartApps(admin: Want, accountId: number): Array<Want>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 <br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 应用自启动名单数组。从API version 24开始，支持返回是否隐藏UI的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp, 100);
  console.info(`Succeeded in getting auto start apps: ${JSON.stringify(res)}`);
} catch (err) {
  console.error(`Failed to get auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]
```


## getAutoStartApps

```TypeScript
function getAutoStartApps(admin: Want | null, accountId: number): Array<Want>
```

查询指定用户下的开机自启动应用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAutoStartApps(admin: Want | null, accountId: number): Array<Want>--><!--Device-applicationManager-function getAutoStartApps(admin: Want | null, accountId: number): Array<Want>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 <br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | 应用自启动名单数组。支持返回是否隐藏UI的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

try {
  // 参数需根据实际情况进行替换
  let res: Array<Want> = applicationManager.getAutoStartApps(null, 100);
  console.info(`Succeeded in getting auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    // 从API version 24支持
    "parameters": {
      "isHiddenStart": false
    }
  },
  // ...
]
```

