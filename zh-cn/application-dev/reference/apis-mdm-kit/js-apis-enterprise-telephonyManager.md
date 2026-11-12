# @ohos.enterprise.telephonyManager (通话管理)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

本模块提供通话管理能力。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅适用于Stage模型。
>
> 本模块接口仅对设备管理应用开放，调用接口前需激活该应用，详情请参考[MDM Kit开发指南](../../mdm/mdm-kit-guide.md)。
>
> 全局通用限制类策略由restrictions提供，若要全局禁用通话，请参考[@ohos.enterprise.restrictions (限制类策略)](js-apis-enterprise-restrictions.md)。

## 导入模块

```ts
import { telephonyManager } from '@kit.MDMKit';
```

## telephonyManager.setSimDisabled

setSimDisabled(admin: Want, slotId: number): void

禁用指定卡槽的SIM卡。禁用后，无法使用该卡槽的SIM卡接打电话、收发短信、上网。例如，企业设备管理员可在员工离职或设备丢失时，禁用SIM卡防止未授权使用。适用于企业需要限制员工设备通话能力的场景，例如员工离职或设备遗失时防止SIM卡被滥用，保障企业通信安全和成本控制。

> **说明：**
>
> 在多个MDM应用场景下，遵循[从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置要禁用的卡槽ID
  let slotId: number = 0;
  // 禁用指定卡槽的SIM卡
  telephonyManager.setSimDisabled(wantTemp, slotId);
  console.info(`Succeeded in setting slotId: ${slotId} disabled.`);
} catch (err) {
  console.error(`Failed to set slotId disabled. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.setSimEnabled

setSimEnabled(admin: Want, slotId: number): void

解除指定卡槽的SIM卡禁用。使用setSimDisabled禁用SIM卡后，再用setSimEnabled启用SIM卡，需要到设置-移动网络-SIM卡管理界面手动打开SIM卡开关。

> **说明：**
>
> 在多个MDM应用场景下，遵循[从严管控](../../mdm/mdm-kit-multi-mdm.md#规则1从严管控)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   |卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。  |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置要启用的卡槽ID
  let slotId: number = 0;
  // 启用指定卡槽的SIM卡
  telephonyManager.setSimEnabled(wantTemp, slotId);
  console.info(`Succeeded in setting slotId: ${slotId} enabled.`);
} catch (err) {
  console.error(`Failed to set slotId enabled. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.isSimDisabled

isSimDisabled(admin: Want, slotId: number): boolean

查询指定卡槽是否禁用。适用于企业管理员需要确认SIM卡禁用策略是否生效的场景，帮助管理员验证策略执行状态，确保通话管控策略正确实施。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                    | 必填 | 说明                                   |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   |卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。  |

**返回值：**

| 类型                               | 说明                      |
| ---------------------------------- | ------------------------- |
| boolean | 指定卡槽的禁用状态。true表示已被禁用，false表示未被禁用。|

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置要查询的卡槽ID
  let slotId: number = 0;
  // 查询指定卡槽的SIM卡是否被禁用
  let result: boolean = telephonyManager.isSimDisabled(wantTemp, slotId);
  console.info(`Succeeded in querying slotId: ${slotId} is disabled or not, result: ${result}`);
} catch (err) {
  console.error(`Failed to query sim is disabled or not. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.addOutgoingCallPolicyNumbers

addOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void

添加通话呼出的允许或禁用名单，如果不添加名单，任意号码都可以呼出，添加后只有名单内的号码允许或禁止呼出。例如，企业可限制员工只能拨打客户服务热线，或禁止拨打特定号码。

以下情况下，通过本接口添加通话呼出的允许或禁用名单，会报策略冲突：

1. 已经通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口禁用了设备通话能力，再通过本接口添加通话呼出的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口解除禁用设备通话能力后，可解除冲突。
2. 已经通过本接口设置了通话呼出的禁用名单，再通过本接口添加通话呼出允许名单，返回9200010错误码。通过[removeOutgoingCallPolicyNumbers](#telephonymanagerremoveoutgoingcallpolicynumbers)接口将之前设置的通话呼出禁用名单移除后，可解除冲突。
3. 已经通过本接口设置了通话呼出的允许名单，再通过本接口添加通话呼出禁用名单，返回9200010错误码。通过[removeOutgoingCallPolicyNumbers](#telephonymanagerremoveoutgoingcallpolicynumbers)接口将之前设置的通话呼出允许名单移除后，可解除冲突。


> **说明：**
>
> 在多个MDM应用场景下，遵循[合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                                                    | 必填 | 说明                                   |
| --------- | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |
| numbers | Array\<string>    | 是   | 通话号码列表，当前仅支持全号码匹配。数组总长度不能超过1000。例如，若当前允许名单数组中已有100个号码，则最多支持通过该接口再添加900个。  |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 9200012  | Parameter verification failed.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 设置要添加到禁用名单的通话号码
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  // 添加通话呼出禁用名单
  telephonyManager.addOutgoingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in adding outgoing call policy.');
} catch (err) {
  console.error(`Failed to add outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.removeOutgoingCallPolicyNumbers

removeOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void

移除通话呼出的允许或禁用名单，若在该名单尚未设置时进行移除，则会移除失败。例如，企业可在解除通话限制、恢复员工正常通话权限时使用。

以下情况下，通过本接口移除通话呼出的允许或禁用名单，会报策略冲突：

已经通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口禁用了设备通话能力，再通过本接口移除通话呼出的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口解除禁用设备通话能力后，可解除冲突。


> **说明：**
>
> 在多个MDM应用场景下，遵循[合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                    | 必填 | 说明                                   |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |
| numbers | Array\<string>    | 是   | 待移除的通话号码数组。数组总长度不能超过1000。  |


**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 设置要从禁用名单中移除的通话号码
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  // 移除通话呼出禁用名单中的指定号码
  telephonyManager.removeOutgoingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in removing outgoing call policy.');
} catch (err) {
  console.error(`Failed to remove outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.getOutgoingCallPolicyNumbers

getOutgoingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>

获取通话呼出的允许或禁用名单。

本接口通过传入Want查询对应企业设备管理应用设置的策略，如需查询实际生效的策略，请使用[telephonyManager.getOutgoingCallPolicyNumbers](#telephonymanagergetoutgoingcallpolicynumbers-1)接口。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                    | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。|
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。 BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。  |


**返回值：**

| 类型                                     | 说明                    |
| ---------------------------------------- | ----------------------- |
| Array\<string> | 通话呼出禁用或允许名单的号码数组。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 获取通话呼出禁用名单
  let numbers: Array<string> = telephonyManager.getOutgoingCallPolicyNumbers(wantTemp, policy);
  console.info(`Succeeded in getting outgoing call policy. result: ${JSON.stringify(numbers)}`);
} catch (err) {
  console.error(`Failed to get outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}
```


## telephonyManager.getOutgoingCallPolicyNumbers

getOutgoingCallPolicyNumbers(admin: Want | null, policy: adminManager.Policy): Array\<string>

获取通话呼出的允许或禁用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                    | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。<br>当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。|
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。 BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。  |

**返回值：**

| 类型                                     | 说明                    |
| ---------------------------------------- | ----------------------- |
| Array\<string> | 通话呼出禁用或允许名单的号码数组。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { adminManager, telephonyManager } from '@kit.MDMKit';

try {
  // 设置策略类型为禁用名单
  // 参数需根据实际情况进行替换
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 获取通话呼出禁用名单
  let numbers: Array<string> = telephonyManager.getOutgoingCallPolicyNumbers(null, policy);
  console.info(`Succeeded in getting outgoing call policy. result: ${JSON.stringify(numbers)}`);
} catch (err) {
  console.error(`Failed to get outgoing call policy. Code: ${err.code}, message: ${err.message}`);
}
```
## telephonyManager.addIncomingCallPolicyNumbers

addIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void

添加通话呼入的允许或禁用名单，如果不添加名单，则任意号码都可以呼入，添加后仅名单内的号码允许或禁止呼入。例如，企业可限制员工只能接听客户来电，或禁止接听骚扰电话。

以下情况下，通过本接口添加通话呼入的允许或禁用名单，会报策略冲突：

1. 已经通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口禁用了设备通话能力，再通过本接口添加通话呼入的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口解除禁用设备通话能力后，可解除冲突。
2. 已经通过本接口设置了通话呼入的禁用名单，再通过本接口添加通话呼入允许名单，返回9200010错误码。通过[removeIncomingCallPolicyNumbers](#telephonymanagerremoveincomingcallpolicynumbers)接口将之前设置的通话呼入禁用名单移除后，可解除冲突。
3. 已经通过本接口设置了通话呼入的允许名单，再通过本接口添加通话呼入禁用名单，返回9200010错误码。通过[removeIncomingCallPolicyNumbers](#telephonymanagerremoveincomingcallpolicynumbers)接口将之前设置的通话呼入允许名单移除后，可解除冲突。

> **说明：**
>
> 在多个MDM应用场景下，遵循[合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名    | 类型                                                    | 必填 | 说明                                   |
| --------- | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |
| numbers | Array\<string>    | 是   | 通话号码列表，当前仅支持全号码匹配。数组总长度不能超过1000。例如，若当前允许名单数组中已有100个号码，则最多支持通过该接口再添加900个。  |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured.                       |
| 9200012  | Parameter verification failed.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 设置要添加到禁用名单的通话号码
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  // 添加通话呼入禁用名单
  telephonyManager.addIncomingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in adding incoming call policy.');
} catch (err) {
  console.error(`Failed to add incoming call policy. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.removeIncomingCallPolicyNumbers

removeIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy, numbers: Array\<string>): void

移除通话呼入的允许或禁用名单，若在该名单尚未设置时进行移除，则会移除失败。例如，企业可在解除呼入通话限制、恢复员工正常接听权限时使用。

以下情况下，通过本接口移除通话呼入的允许或禁用名单，会报策略冲突：

1. 已经通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口禁用了设备通话能力，再通过本接口移除通话呼入的禁用或允许名单，返回203错误码。通过[setDisallowedPolicy](js-apis-enterprise-restrictions.md#restrictionssetdisallowedpolicydeprecated)接口解除禁用设备通话能力后，可解除冲突。


> **说明：**
>
> 在多个MDM应用场景下，遵循[合并](../../mdm/mdm-kit-multi-mdm.md#规则4合并)规则。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型                                                    | 必填 | 说明                                   |
| ------ | ------------------------------------------------------- | ---- | -------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |
| numbers | Array\<string>    | 是   | 待移除的通话号码数组。数组总长度不能超过1000。   |


**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                       |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 设置要从禁用名单中移除的通话号码
  let numbers: Array<string> = [
    // 需根据实际情况进行替换
    "13112345678"
  ];
  // 移除通话呼入禁用名单中的指定号码
  telephonyManager.removeIncomingCallPolicyNumbers(wantTemp, policy, numbers);
  console.info('Succeeded in removing incoming call policy.');
} catch (err) {
  console.error(`Failed to remove incoming call policy. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.getIncomingCallPolicyNumbers

getIncomingCallPolicyNumbers(admin: Want, policy: adminManager.Policy): Array\<string>

获取通话呼入的允许或禁用名单。

本接口通过传入Want查询对应企业设备管理应用设置的策略，如需查询实际生效的策略，请使用[telephonyManager.getIncomingCallPolicyNumbers](#telephonymanagergetincomingcallpolicynumbers-1)接口。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                    | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。|
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |


**返回值：**

| 类型                                     | 说明                    |
| ---------------------------------------- | ----------------------- |
| Array\<string> | 通话呼入禁用或允许名单的号码数组。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { adminManager, telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 设置策略类型为禁用名单
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 获取通话呼入禁用名单
  let numbers: Array<string> = telephonyManager.getIncomingCallPolicyNumbers(wantTemp, policy);
  console.info(`Succeeded in getting incoming call policy. result: ${JSON.stringify(numbers)}`);
} catch (err) {
  console.error(`Failed to get incoming call policy. Code: ${err.code}, message: ${err.message}`);
}
```


## telephonyManager.getIncomingCallPolicyNumbers

getIncomingCallPolicyNumbers(admin: Want | null, policy: adminManager.Policy): Array\<string>

获取通话呼入的允许或禁用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名     | 类型                                                    | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。<br>当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。|
| policy | [adminManager.Policy](js-apis-enterprise-adminManager.md#policy20)    | 是   | 允许或禁用名单策略。BLOCK_LIST为禁用名单，TRUST_LIST为允许名单。   |

**返回值：**

| 类型                                     | 说明                    |
| ---------------------------------------- | ----------------------- |
| Array\<string> | 通话呼入禁用或允许名单的号码数组。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { adminManager, telephonyManager } from '@kit.MDMKit';

try {
  // 设置策略类型为禁用名单
  // 参数需根据实际情况进行替换
  let policy: adminManager.Policy = adminManager.Policy.BLOCK_LIST;
  // 获取通话呼入禁用名单
  let numbers: Array<string> = telephonyManager.getIncomingCallPolicyNumbers(null, policy);
  console.info(`Succeeded in getting incoming call policy. result: ${JSON.stringify(numbers)}`);
} catch (err) {
  console.error(`Failed to get incoming call policy. Code: ${err.code}, message: ${err.message}`);
}
```
## telephonyManager.hangupCalling<sup>23+</sup>

hangupCalling(admin: Want): void

挂断当前通话。仅支持运营商通话，不包括畅联等。例如，企业设备管理员可在企业安全管理场景中，强制挂断员工正在进行的不合规通话。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 挂断当前通话
  telephonyManager.hangupCalling(wantTemp);
} catch (err) {
  console.error(`Failed to hang up calling. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.activeSim

activeSim(admin: Want, slotId: number): void

启用指定卡槽的SIM卡。启用该SIM卡，SIM卡菜单项开启，用于设备已经插入SIM卡但是并未启用的场景，可以通过该接口启用SIM卡，无需用户手动启用。SIM卡启用后可以使用该SIM卡进行通信。该接口需要插入SIM卡并关闭飞行模式才能成功调用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201017  | SIM card activation or deactivation failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 设置要启用的卡槽ID
let slotId: number = 0;
try {
  // 启用指定卡槽的SIM卡
  telephonyManager.activeSim(wantTemp, slotId);
  console.info(`success in activating SIM card on slot ${slotId}`);
} catch (err) {
  console.error(`Failed to activate SIM on slot ${slotId}. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.deactiveSim

deactiveSim(admin: Want, slotId: number): void

停用指定卡槽SIM卡。停用该SIM卡，SIM卡菜单项关闭，无法使用该卡槽的SIM卡接打电话，收发短信，上网。例如，企业可在员工休假或设备维护期间，临时停用SIM卡。该接口需要插入SIM卡并关闭飞行模式才能成功调用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201017  | SIM card activation or deactivation failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 设置要停用的卡槽ID
let slotId: number = 0;
try {
  // 停用指定卡槽的SIM卡
  telephonyManager.deactiveSim(wantTemp, slotId);
  console.info(`success in deactivating SIM card on slot ${slotId}`);
} catch (err) {
  console.error(`Failed to deactivate SIM on slot ${slotId}. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.setDefaultData

setDefaultData(admin: Want, slotId: number): void

设置指定卡槽的SIM卡为默认数据流量卡，设备将使用指定卡槽的SIM卡流量上网。例如，企业可在双卡设备管理场景中，为员工设备指定默认的数据流量卡以统一管理流量使用。该接口需要插入SIM卡并关闭飞行模式才能成功调用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number                     | 是   | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201020  | Failed to set the default data SIM card. The airplane mode is enabled or no SIM card is inserted. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 设置要作为默认数据流量卡的卡槽ID
let slotId: number = 0;
try {
  // 设置指定卡槽为默认数据流量卡
  telephonyManager.setDefaultData(wantTemp, slotId);
  console.info(`success in setting default data SIM ID on slot ${slotId}`);
} catch (err) {
  console.error(`Failed to set default data on slot ${slotId}. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.getDefaultData

getDefaultData(admin: Want): number

获取设备当前默认使用的数据流量卡卡槽ID。例如，企业设备管理员可在设备管理过程中查询当前配置的默认数据流量卡，以便进行流量管理或切换数据卡配置。未插卡或者飞行模式下会获取上一次使用的数据流量卡卡槽ID、设备从未设置过默认数据流量卡场景下，该接口返回默认卡槽1，值为0。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**设备行为差异：** 该接口在Phone和Tablet设备中可正常调用，在其他设备中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型                               | 说明                      |
| ---------------------------------- | ------------------------- |
| number | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。|

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 203      | This function is prohibited by enterprise management policies. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**示例：**

```ts
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let slotId: number = 0;
try {
  // 获取当前默认数据流量卡的卡槽ID
  slotId = telephonyManager.getDefaultData(wantTemp);
  console.info(`success in getting default data SIM ID on slot ${slotId}`);
} catch (err) {
  console.error(`Failed to get default data on slot ${slotId}. Code: ${err.code}, message: ${err.message}`);
}
```

## telephonyManager.getCallLogs
 
getCallLogs(queryConfig: TelephonyQueryConfig): Promise\<Array\<CallLogInfo\>\>
 
根据指定的时间范围和电话号码查询通话记录。企业MDM应用可通过此接口读取设备通话记录进行审计。支持按时间范围和号码进行筛选查询。查询时间范围不能超过31天，当前支持后缀匹配。通话记录最多保存5000条，超过时自动删除最早的记录。使用Promise异步回调。

> **说明：**
>
> 在接入、使用本能力前，您需要在隐私政策中向用户告知收集的个人信息类型（通话记录、电话号码）、使用目的及隐私政策链接等信息，并获取用户的同意或取得其他合法性基础。
> 本接口查询的通话记录属于用户敏感数据。首次查询通话记录时，系统会向设备用户发送敏感内容访问通知，告知用户企业设备管理应用正在查询通话记录。建议企业管理员提前告知终端用户。

**起始版本：** 26.1.0
 
**需要权限：** ohos.permission.ENTERPRISE_READ_CALL_LOG
 
**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
 
**模型约束：** 此接口仅可在Stage模型下使用。
 
**参数：**
 
| 参数名       | 类型                                            | 必填 | 说明                                                         |
| ------------ | ----------------------------------------------- | ---- | ------------------------------------------------------------ |
| queryConfig  | [TelephonyQueryConfig](#telephonyqueryconfig)   | 是   | 查询配置，包括时间范围和电话号码。telephoneNumber未传或为空字符串时不按号码过滤，返回时间范围内全部通话记录。 |
 
**返回值：**
 
| 类型                       | 说明                                   |
| -------------------------- | -------------------------------------- |
| Promise\<Array\<[CallLogInfo](#callloginfo)\>\> | Promise对象，返回符合查询条件的通话记录列表。 |
 
**错误码**：
 
以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。
 
| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9200016  | Service timeout. |
 
**示例：**
 
```ts
import { telephonyManager } from '@kit.MDMKit';
 
let queryConfig: telephonyManager.TelephonyQueryConfig = {
  startTime: Math.floor(Date.now() / 1000) - 7 * 24 * 60 * 60, // 查询最近7天的通话记录（秒级时间戳）
  endTime: Math.floor(Date.now() / 1000),
  telephoneNumber: '138xxxxxxxx' // 可选，按号码过滤
};
 
async function queryCallLogs() {
  try {
    // 异步查询通话记录
    let callLogs: Array<telephonyManager.CallLogInfo> = await telephonyManager.getCallLogs(queryConfig);
    console.info('Succeeded in getting call logs.');
    for (let log of callLogs) {
      console.info(`Call: number=${log.telephoneNumber}, incoming=${log.isIncoming}, slot=${log.slotId}`);
      console.info(`createTime=${log.createTime}, start=${log.startTime}, end=${log.endTime}`);
    }
  } catch (err) {
    console.error(`Failed to get call logs. Code: ${err.code}, message: ${err.message}`);
  }
}

queryCallLogs();
```

## telephonyManager.getSmsMessages

getSmsMessages(queryConfig: TelephonyQueryConfig): Promise\<Array\<SmsMessageInfo>>

根据指定的时间范围和电话号码查询短信消息。企业MDM应用可通过此接口读取设备短信内容进行审计，支持按时间范围和号码进行筛选查询。如果未查询到符合条件的短信，返回空数组。查询短信容量最大为128M。适用于企业需要对设备的短信进行审计等场景。

> **说明：**
>
> 在接入、使用本能力前，您需要在隐私政策中向用户告知收集的个人信息类型（短信内容、电话号码）、使用目的及隐私政策链接等信息，并获取用户的同意或取得其他合法性基础。
> 本接口查询的短信内容属于用户敏感数据。首次调用本接口查询短信时，系统会向设备用户发送敏感内容访问通知，告知用户企业设备管理应用正在查询短信内容。建议企业管理员提前告知终端用户。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_READ_MESSAGES

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名       | 类型                                                    | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| queryConfig  | [TelephonyQueryConfig](#telephonyqueryconfig)                                    | 是   | 查询选项，包括时间范围和电话号码。时间范围是0到当前时间戳、单位是秒。                           |

**返回值：**

| 类型                               | 说明                      |
| ---------------------------------- | ------------------------- |
| Promise\<Array\<[SmsMessageInfo](#smsmessageinfo)>> | Promise对象，返回符合查询条件的短信消息列表。 |

**错误码**：

以下错误码的详细介绍请参见[企业设备管理错误码](errorcode-enterpriseDeviceManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 9200016  | Service timeout.                                             |

**示例：**

```ts
import { telephonyManager } from '@kit.MDMKit';

let queryConfig: telephonyManager.TelephonyQueryConfig = {
  startTime: Math.floor(Date.now() / 1000) - 7 * 24 * 60 * 60, // 查询最近7天的短信（秒级时间戳）
  endTime: Math.floor(Date.now() / 1000),
  telephoneNumber: ''
};

telephonyManager.getSmsMessages(queryConfig).then((result) => {
  console.info(`Succeeded in getting SMS messages, result:${JSON.stringify(result)}`);
}).catch((err) => {
  console.error(`Failed to get SMS messages. Code: ${err.code}, message: ${err.message}`);
});
```

## TelephonyQueryConfig

短信和通话记录查询配置。提供通话/短信类查询的通用查询参数，包括时间范围和电话号码。startTime需小于等于endTime；如需查询全部记录，可传入startTime为0、endTime为当前时间戳。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称            | 类型   | 只读 | 可选 | 说明                                                              |
| --------------- | ------ | ---- | ---- | ----------------------------------------------------------------- |
| startTime       | number | 否   | 否   | 查询起始时间（时间戳，单位为秒），按通话/短信记录的创建时间匹配。 |
| endTime         | number | 否   | 否   | 查询结束时间（时间戳，单位为秒），按通话/短信记录的创建时间匹配。 |
| telephoneNumber | string | 否   | 是   | 过滤电话号码，过滤规则是后缀匹配。默认值为空字符串，表示查询所有记录。                |

## SmsMessageInfo

短信消息信息。提供短信的详细信息，包括消息内容、发送方/接收方信息和时间戳。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称            | 类型    | 只读 | 可选 | 说明                                                        |
| --------------- | ------- | ---- | ---- | ----------------------------------------------------------- |
| time            | number  | 否   | 否   | 短信接收/发送时间（时间戳，单位：秒）。                           |
| isSender        | boolean | 否   | 否   | 短信方向：**true**表示发送，**false**表示接收。             |
| telephoneNumber | string  | 否   | 否   | 对方电话号码。                                              |
| content         | string  | 否   | 否   | 短信内容。单条短信长度无限制、查询总短信容量不超过128M。                |

## CallLogInfo
 
通话记录信息。提供通话记录的详细信息，包括通话时长、通话方向（呼入/呼出）、时间戳以及使用的SIM卡槽位。
 
**起始版本：** 26.1.0
 
**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**模型约束：** 此接口仅可在Stage模型下使用。
 
| 名称              | 类型    | 只读 | 可选 | 说明                                                      |
| ----------------- | ------- | ---- | ---- | --------------------------------------------------------- |
| createTime        | number  | 是   | 否   | 通话记录创建时间（时间戳，单位：秒）。来电时为开始振铃时刻，去电时为拨出时刻。 |
| startTime         | number  | 是   | 否   | 通话接通时间（时间戳，单位：秒）。通话未接通时为0。          |
| endTime           | number  | 是   | 否   | 通话结束时间（时间戳，单位：秒）。通话未接通时为挂断时间。    |
| isIncoming        | boolean | 是   | 否   | 通话方向：**true** 表示来电（呼入），**false** 表示去电（呼出）。   |
| slotId            | number  | 是   | 否   | 卡槽ID。0表示卡槽1，1表示卡槽2。                      |
| telephoneNumber   | string  | 是   | 否   | 对方电话号码。                                            |