# @ohos.userIAM.companionDeviceAuth (伴随设备认证)(系统接口)
<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

## 模块简介

**companionDeviceAuth**模块是OpenHarmony用户身份认证体系（UserIAM）的重要组成部分，专门用于伴随设备认证管理。该模块为系统应用提供伴随设备查询、订阅和服务范围管理等能力。

该模块主要用于以下场景：
- 管理伴随设备与主设备之间的认证关系。
- 查询和订阅伴随设备的状态变化。
- 管理伴随设备支持的业务范围。
- 实现持续认证功能。
- 处理设备选择和注册。

> **说明：**
> 
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。

## 关键Class/Interface介绍

### 核心枚举类型

- **[BusinessId](#businessid)**：业务ID枚举，用于标识伴随设备支持的业务场景（如免解锁执行语音指令等）。
- **[DeviceIdType](#deviceidtype)**：设备ID类型枚举（如统一设备ID）。
- **[SelectPurpose](#selectpurpose)**：选择伴随设备的目的（如添加模板、认证设备选择）。

### 核心接口类型

- **[DeviceKey](#devicekey)**：设备关键信息接口，包含设备ID类型、设备ID和设备用户ID。
- **[DeviceStatus](#devicestatus)**：设备状态接口，包含设备密钥、设备用户名、设备型号、设备名称、在线状态和支持的服务ID列表。
- **[TemplateStatus](#templatestatus)**：模板状态接口，包含模板ID、实时数据标识、有效性标识、本地用户ID、添加时间、支持的服务ID列表和设备状态。
- **[ContinuousAuthParam](#continuousauthparam)**：持续认证参数接口。
- **[DeviceSelectResult](#deviceselectresult)**：设备选择结果接口。

### 核心回调类型

- **[TemplateStatusCallback](#templatestatuscallback)**：模板状态回调。
- **[ContinuousAuthStatusCallback](#continuousauthstatuscallback)**：持续认证状态回调。
- **[AvailableDeviceStatusCallback](#availabledevicestatuscallback)**：可用设备状态回调。
- **[DeviceSelectCallback](#deviceselectcallback)**：设备选择回调。

### 核心类

- **[StatusMonitor](#statusmonitor)**：状态监听器类，用于查询和订阅协同模板信息。

![类关系图](figures/uml_companiondeviceauth.png)

## API组合使用关系说明

使用companionDeviceAuth模块的典型流程如下：

```ts
// 以下为阐述调用逻辑的伪代码，仅提供步骤说明，不提供详细的可执行代码。
// 1. 获取状态监听器。
let statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);

// 2. 获取当前模板状态。
let templateStatusList = await statusMonitor.getTemplateStatus();

// 3. 订阅模板状态变化事件。
statusMonitor.onTemplateChange((templateStatusList) => {
  // 处理模板状态变化。
});

// 4. 订阅可用设备变化事件。
statusMonitor.onAvailableDeviceChange((deviceStatusList) => {
  // 处理设备状态变化。
});

// 5. 订阅持续认证状态变化。
let authParam = { templateId: specificTemplateId };
statusMonitor.onContinuousAuthChange(authParam, (isAuthPassed, authTrustLevel) => {
  // 处理持续认证状态变化。
});

// 6. 注册设备选择回调。
companionDeviceAuth.registerDeviceSelectCallback((selectPurpose) => {
  // 返回设备选择结果。
  return deviceSelectResult;
});

// 7. 更新模板支持的服务范围。
await companionDeviceAuth.updateEnabledBusinessIds(templateId, enabledBusinessIds);

// 8. 使用完成后取消订阅和注销回调。
statusMonitor.offTemplateChange();
statusMonitor.offAvailableDeviceChange();
statusMonitor.offContinuousAuthChange();
companionDeviceAuth.unregisterDeviceSelectCallback();
```

## 导入模块

```ts
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## BusinessId

业务ID枚举。业务ID是伴随设备支持的某个业务场景的唯一标识。不同的伴随设备由于认证安全性差异，支持的业务场景范围也不同，例如免解锁执行语音指令。

不同业务ID的伴随设备关系是独立的，互不干扰，可以独立添加、删除、认证。

当前伴随设备模块的业务有：OH默认业务、锁屏解锁、解锁应用锁以及语音指令在锁屏执行前的身份鉴权等。

业务的添加对于服务端设备支持的场景有要求，如多屏协同业务，要求服务端设备支持委托认证场景。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| ----------- | ---- | ---------- |
| DEFAULT | 0 | 默认业务ID。系统预设的默认业务标识，用于基本的伴随设备认证场景。 |
| VENDOR_BEGIN | 10000 | 厂商自定义业务标识取值起点。厂商可在此值基础上自定义扩展业务ID，实际取值需大于等于10000，避免与系统保留值\[0-9999\]冲突。 |

## DeviceIdType

设备ID类型枚举。用于定义设备业务标识的类型，支持系统预设类型和厂商自定义扩展类型。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| ----------------- | ----- | ------------------------------------------------------------ |
| UNIFIED_DEVICE_ID | 1 | 统一设备ID。系统预设的设备业务标识类型，用于跨设备的统一设备识别。 |
| VENDOR_BEGIN | 10000 | 厂商自定义设备ID类型取值起点。厂商可在此值基础上自定义扩展设备ID类型，实际取值需大于等于10000，避免与系统保留值[1-9999]冲突。 |

## SelectPurpose

选择伴随设备的目的。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| ----------- | ---- | ---------- |
| SELECT_ADD_DEVICE | 1 | 选择添加模板的伴随设备。表示当前操作目的是选择一个设备用于添加新的认证模板，系统应返回适合添加模板的设备列表。 |
| SELECT_AUTH_DEVICE | 2 | 选择提供认证能力的伴随设备。表示当前操作目的是选择一个已注册模板的设备用于执行身份认证，系统应返回具备认证能力的设备列表。 |
| VENDOR_BEGIN | 10000 | 厂商自定义选择目的取值起点。厂商可在此值基础上自定义扩展选择目的，实际取值需大于等于10000，避免与系统保留值\[0-9999\]冲突。 |

## DeviceKey

设备业务标识。用于唯一标识一个设备及其用户，包含设备ID类型、设备ID和设备用户ID等信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------------ | ---------- | ---- | ---- | -------------------- |
| deviceIdType | number | 否 | 否 | 设备ID类型。用于指定设备业务标识的类型，可在[DeviceIdType](#deviceidtype)基础上自定义扩展，如使用UNIFIED_DEVICE_ID(1)表示统一设备ID，或使用厂商自定义值（≥10000）。 |
| deviceId | string | 否 | 否 | 设备ID。设备的唯一标识字符串，具体格式由deviceIdType决定。 |
| deviceUserId | number | 否 | 否 | 设备用户ID。设备上的用户标识，为大于等于0的正整数，用于区分设备上的不同用户。 |

## DeviceStatus

设备状态信息。用于描述伴随设备的当前状态，包括设备业务标识、用户名、型号信息、设备名、在线状态以及支持的业务ID列表等。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------------------- | ------------------------- | ---- | ---- | ---------------------- |
| deviceKey | [DeviceKey](#devicekey) | 否 | 否 | 设备关键信息。包含设备ID类型、设备ID和设备用户ID，作为设备的唯一标识。 |
| deviceUserName | string | 否 | 否 | 设备用户名。设备上当前用户的显示名称，用于在设备选择界面展示。 |
| deviceModelInfo | string | 否 | 否 | 设备模型信息。设备的型号标识，如产品型号、设备类型等信息。 |
| deviceName | string | 否 | 否 | 设备名。设备的名称或别名，用于在设备列表中展示给用户。 |
| isOnline | boolean | 否 | 否 | 设备在线状态。true表示设备处于在线状态，可以与主设备通信；false表示设备处于离线状态，无法进行认证交互。 |
| supportedBusinessIds | number[] | 否 | 否 | 设备支持的业务ID列表。表示该设备支持的业务场景范围，如解锁锁屏、解锁应用锁等。不同设备因认证安全性差异，支持的业务范围不同。 |

## TemplateStatus

用于描述已注册的伴随设备认证模板的完整状态信息，包括模板ID、数据确认状态、有效性、用户ID、添加时间、支持的业务范围以及关联的设备状态等。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------------------ | ------------------------------- | ---- | ---- | -------------------- |
| templateId | Uint8Array | 否 | 否 | 模板ID。伴随设备认证模板的唯一标识，用于在更新业务范围或订阅认证状态时指定目标模板。 |
| isConfirmed | boolean | 否 | 否 | 数据确认状态。true表示数据是实时数据，已与设备确认同步；false表示数据是缓存数据，可能与设备实际状态存在差异。 |
| isValid | boolean | 否 | 否 | 模板有效性。true表示模板有效，可用于认证；false表示模板无效，可能已被删除或失效，无法用于认证。 |
| localUserId | number | 否 | 否 | 本地用户ID。主设备上与该模板关联的用户标识，为大于等于0的正整数。 |
| addedTime | Date | 否 | 否 | 模板添加时间。模板创建的时间戳，格式为Unix时间戳，即自1970年1月1日起经过的毫秒数。 |
| enabledBusinessIds | number[] | 否 | 否 | 支持的业务ID列表。该模板已启用的业务场景范围，可通过[updateEnabledBusinessIds](#companiondeviceauthupdateenabledbusinessids)接口更新。 |
| deviceStatus | [DeviceStatus](#devicestatus) | 否 | 否 | 设备状态信息。与该模板关联的伴随设备的当前状态，包括在线状态、设备名等。 |

## TemplateStatusCallback

type TemplateStatusCallback = (templateStatusList: TemplateStatus[]) => void

回调函数，用于接收模板状态变化通知。当模板状态发生变化（如添加、删除、有效性变更等）时，系统会通过此回调通知应用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型  | 必填 | 说明 |
| ------------------ | ------------------------------------- | ---- | -------------- |
| templateStatusList | [TemplateStatus](#templatestatus)[] | 是 | 模板状态列表。包含当前用户下所有已注册模板的状态信息，应用可根据列表中的isValid字段判断模板有效性，根据isConfirmed字段判断数据是否为实时数据。 |

## ContinuousAuthStatusCallback

type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void

回调函数，用于接收持续认证状态变化通知。当伴随设备的认证状态发生变化时，系统会通过此回调通知应用当前的认证结果和认证可信等级。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------------- | ----------------------- | ---- | ------------------------------------------------------------ |
| isAuthPassed | boolean | 是 | 认证是否通过。true表示伴随设备认证通过，用户身份已确认；false表示认证未通过，用户身份未确认或认证已失效。 |
| authTrustLevel | [UserAuth.AuthTrustLevel](./js-apis-useriam-userauth.md#authtrustlevel8) | 否 | 伴随设备当前能达到的最高认证可信等级。值为ATL1（10000）、ATL2（20000）、ATL3（30000）或ATL4（40000），等级越高表示认证安全性越强。<br>**说明**：<br>仅当isAuthPassed为true时提供此参数。<br>典型操作需要的身份认证可信等级，具体请参见[认证可信等级划分原则](../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。 |

## AvailableDeviceStatusCallback

type AvailableDeviceStatusCallback = (deviceStatusList: DeviceStatus[]) => void

回调函数，用于接收可添加的设备列表变化通知。当可添加的伴随设备列表发生变化（如新设备上线、设备离线等）时，系统会通过此回调通知应用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---------------- | --------------------------------- | -------------- | -------------- |
| deviceStatusList | [DeviceStatus](#devicestatus)[] | 是 | 设备状态列表。包含当前可添加为伴随设备的所有设备状态信息。应用可根据isOnline字段筛选在线设备，根据supportedBusinessIds字段判断设备支持的业务范围。 |

## ContinuousAuthParam

持续认证参数。用于配置订阅持续认证状态时的相关参数，如指定订阅的目标模板。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---------- | ---------- | ---- | ---- | -------------------------------------------- |
| templateId | Uint8Array | 否 | 是 | 模板ID。用于指定订阅的目标模板。若不指定此参数，默认订阅当前用户下全部模板的持续认证状态。指定具体模板ID时，仅订阅该模板的认证状态变化。 |

## StatusMonitor

状态监听器对象。用于监听或获取模板状态、持续认证状态、可添加设备状态等信息。通过[getStatusMonitor](#companiondeviceauthgetstatusmonitor)获取此对象。

### getTemplateStatus

getTemplateStatus(): Promise&lt;TemplateStatus[]&gt;

获取伴随设备模板状态。用于查询当前用户下所有已注册的伴随设备认证模板的状态信息，包括模板有效性、支持的业务范围、关联设备状态等。使用Promise异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| ------------------------------------- | ------------------------------------------------------ |
| Promise&lt;[TemplateStatus](#templatestatus)[]&gt;| Promise对象，成功时返回当前用户下全部模板的状态列表，每个模板状态包含模板ID、有效性、设备信息等；失败时抛出相应错误码。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
statusMonitor.getTemplateStatus()
  .then((templateStatus) => {
    console.info(`templateStatus: ${JSON.stringify(templateStatus)}`);
  })
  .catch((error: BusinessError) => {
    console.error(`error has been captured: message:${error?.message}`);
  })
```

### onTemplateChange

onTemplateChange(callback: TemplateStatusCallback): void

订阅模板的状态变化。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | --------------------------------------------------- | ---- | ---------------------------- |
| callback | [TemplateStatusCallback](#templatestatuscallback) | 是 | 回调函数，用于接收模板状态。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (templates: companionDeviceAuth.TemplateStatus[]): void => {
    console.info('template status updated');
  };
  statusMonitor.onTemplateChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offTemplateChange

offTemplateChange(callback?: TemplateStatusCallback): void

取消订阅模板的状态变化。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [TemplateStatusCallback](#templatestatuscallback) | 否 | 指定取消注册的回调函数。若不填此参数，则取消onTemplateChange注册的全部回调。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (templates: companionDeviceAuth.TemplateStatus[]): void => {
    console.info('template status updated');
  };
  statusMonitor.onTemplateChange(handler);
  statusMonitor.offTemplateChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### onAvailableDeviceChange

onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void

订阅可添加的伴随设备状态变化。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------- |
| callback | [AvailableDeviceStatusCallback](#availabledevicestatuscallback) | 是 | 处理可选设备更新的回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (deviceStatusList: companionDeviceAuth.DeviceStatus[]): void => {
    console.info('available device changed');
  };
  statusMonitor.onAvailableDeviceChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offAvailableDeviceChange

offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void

取消订阅可添加的伴随设备状态变化，使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ------------------------------------------------------------ | ---- | -------------------- |
| callback | [AvailableDeviceStatusCallback](#availabledevicestatuscallback) | 否 | 需要取消的目标回调。不传入callback时默认移除当前应用注册的全部相关回调。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localUserId = 100;
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const handler = (deviceStatusList: companionDeviceAuth.DeviceStatus[]): void => {
    console.info('available device changed');
  };
  statusMonitor.onAvailableDeviceChange(handler);
  statusMonitor.offAvailableDeviceChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### onContinuousAuthChange

onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void

订阅伴随设备的持续认证状态。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| param | [ContinuousAuthParam](#continuousauthparam) | 是 | 用于指定订阅的设备。 |
| callback | [ContinuousAuthStatusCallback](#continuousauthstatuscallback) | 是 | 订阅的设备持续认证状态发生变化时执行此回调。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The template is not found. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: userAuth.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

### offContinuousAuthChange

offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void

取消订阅伴随设备的持续认证状态变化事件。取消后，应用将不再接收持续认证状态变化通知。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [ContinuousAuthStatusCallback](#continuousauthstatuscallback) | 否 | 指定取消注册的回调函数。若传入此参数，仅取消该特定回调的注册；若不传入此参数，则取消onContinuousAuthChange注册的全部回调。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: userAuth.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
  statusMonitor.offContinuousAuthChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

## companionDeviceAuth.getStatusMonitor

getStatusMonitor(localUserId: number): StatusMonitor

获取状态监听器。用于获取指定用户的状态监听器对象，通过该对象可查询和订阅伴随设备的模板状态、持续认证状态、可添加设备状态等信息。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----------- | ---- | ---- | ------------ |
| localUserId | number | 是 | 本地用户ID。主设备上的用户标识，为大于等于0的正整数。用于获取该用户对应的伴随设备状态监听器。 |

**返回值：**

| 类型 | 说明 |
| --------------------------------- | ------------------------------ |
| [StatusMonitor](#statusmonitor) | 状态监听器对象。可用于查询模板状态（[getTemplateStatus](#gettemplatestatus)）、订阅模板变化（[onTemplateChange](#ontemplatechange)）、订阅可添加设备变化（[onAvailableDeviceChange](#onavailabledevicechange)）、订阅持续认证状态（[onContinuousAuthChange](#oncontinuousauthchange)）等操作。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The local user is not found. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userAuth } from '@kit.UserAuthenticationKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: userAuth.AuthTrustLevel): void => {
    console.info('continuous auth changed');
    console.info(`isAuthPassed: ${isAuthPassed}`);
    if (authTrustLevel !== undefined) {
      console.info(`authTrustLevel: ${authTrustLevel}`);
    }
  };

  statusMonitor.onContinuousAuthChange(continuousAuthParam, handler);
  statusMonitor.offContinuousAuthChange(handler);
} catch (error) {
  const message = (error as BusinessError).message;
  console.error(`error has been captured: message:${message}`);
}
```

## DeviceSelectResult

伴随设备选择回调的返回结果。用于在设备选择回调中返回用户选择的设备信息和扩展上下文。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---------------- | --------------------------- | ---- | ---- | ------------------------------------------ |
| deviceKeys | [DeviceKey](#devicekey)[] | 否 | 否 | 设备信息列表。包含用户选择的设备业务标识信息，每个DeviceKey包含设备ID类型、设备ID和设备用户ID。系统会根据这些信息执行后续的添加模板或认证操作。|
| selectionContext | Uint8Array | 否 | 是 | 设备选择上下文。携带JSON格式的扩展信息，可用于传递设备选择过程中的额外参数，如认证配置、业务场景标识等。 |

## DeviceSelectCallback

type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult

伴随设备选择回调函数类型。当系统需要用户选择伴随设备时（如添加模板或执行认证），会调用此回调，应用需返回用户选择的设备信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------- | ---- | ---- | ------------------------------------------------------------ |
| selectPurpose | number | 是 | 选择目的。用于标识当前设备选择的意图，取值参见[SelectPurpose](#selectpurpose)。SELECT_ADD_DEVICE(1)表示选择添加模板的设备，SELECT_AUTH_DEVICE(2)表示选择认证设备。厂商可自定义扩展值（大于等于10000）。应用应根据选择目的返回相应的设备列表。 |

**返回值：**

| 类型 | 说明 |
| ------------------------------------------- | -------------------- |
| [DeviceSelectResult](#deviceselectresult) | 设备选择结果。包含用户选择的设备信息列表（deviceKeys）和可选的扩展上下文（selectionContext）。 |

## companionDeviceAuth.registerDeviceSelectCallback

registerDeviceSelectCallback(callback: DeviceSelectCallback): void

注册伴随设备选择回调。当系统需要用户选择伴随设备时，会调用此回调，应用需在回调中返回用户选择的设备信息。通过此回调，应用可以实现自定义的设备选择逻辑，如弹出设备选择界面让用户选择。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [DeviceSelectCallback](#deviceselectcallback) | 是 | 伴随设备选择回调函数。系统调用时会传入选择目的（selectPurpose），应用需根据目的返回相应的DeviceSelectResult，包含用户选择的设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  companionDeviceAuth.registerDeviceSelectCallback((purpose) => {
    const addDeviceId = 'addDeviceId';
    const otherDeviceId = 'otherDeviceId';
    const addDeviceUserId = 100;
    const otherDeviceUserId = 100;
    if (purpose === companionDeviceAuth.SelectPurpose.SELECT_ADD_DEVICE) {
      return {
        deviceKeys: [{
          deviceIdType: companionDeviceAuth.DeviceIdType.UNIFIED_DEVICE_ID,
          deviceId: addDeviceId,
          deviceUserId: addDeviceUserId
        }]
      };
    }
    return {
      deviceKeys: [{
        deviceIdType: companionDeviceAuth.DeviceIdType.UNIFIED_DEVICE_ID,
        deviceId: otherDeviceId,
        deviceUserId: otherDeviceUserId
      }]
    };
  })
} catch (error) {
  const err = error as BusinessError;
  console.error(`error has been captured: ${err.code} ${err.message}`);
}
```

## companionDeviceAuth.unregisterDeviceSelectCallback

unregisterDeviceSelectCallback(): void

取消注册伴随设备选择回调。取消后，系统将不再调用应用注册的设备选择回调，设备选择将回退到系统默认行为。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**
<!--code_no_check-->

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  companionDeviceAuth.unregisterDeviceSelectCallback();
} catch (error) {
  const err = error as BusinessError;
  console.error(`error has been captured: ${err.code} ${err.message}`);
}
```

## companionDeviceAuth.updateEnabledBusinessIds

updateEnabledBusinessIds(templateId: Uint8Array, enabledBusinessIds: number[]): Promise&lt;void&gt;

更新指定伴随设备模板支持的业务范围。用于修改已注册模板的启用业务ID列表，从而控制该模板可参与的业务场景。使用Promise异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------------ | ---------- | ---- | ------------------------ |
| templateId | Uint8Array | 是 | 目标模板ID。要更新业务范围的模板的唯一标识，可通过[getTemplateStatus](#gettemplatestatus)获取。 |
| enabledBusinessIds | number[] | 是 | 模板支持的业务ID集合。要启用的业务场景列表，如[DEFAULT]、[解锁锁屏业务ID]等。不同业务ID对应不同的认证场景，应用可根据业务需求配置。 |

**返回值：**

| 类型                | 说明            |
| ------------------- | --------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 201 | Permission denied. |
| 202 | Not system application. |
| 32600001 | The system service is not working properly. Please try again later. |
| 32600002 | The template is not found. |
| 32600003 | The business ID is invalid. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const templateId = new Uint8Array([1, 2, 3]);
companionDeviceAuth.updateEnabledBusinessIds(templateId, [companionDeviceAuth.BusinessId.DEFAULT])
  .then(() => {
    console.info('business scope updated');
  })
  .catch((err: BusinessError) => {
    console.error(`error has been captured: code: ${err.code}, message: ${err.message}`);
  })
```
