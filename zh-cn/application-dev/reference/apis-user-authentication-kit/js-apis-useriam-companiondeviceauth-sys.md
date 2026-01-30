# @ohos.userIAM.companionDeviceAuth (伴随设备认证)(系统接口)
面向系统应用提供伴随设备的查询、订阅以及业务范围管理等能力。

伴随设备是用户在主设备上添加的身份认证凭据，在满足条件的情况下能够与主设备交互进行用户身份鉴权。伴随设备应用场景，例如：手表作为伴随设备解锁手机、 耳机作为伴随设备让语音指令在手机上可以免解锁执行等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。

## 导入模块

```ts
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## BusinessId

业务ID是伴随设备支持的某个业务场景的唯一标识。不同的伴随设备由于认证安全性差异，支持的业务场景范围也不同，例如智能手表作为伴随设备可以解锁锁屏、解锁应用锁、支持语音指令在锁屏上执行，而耳机作为伴随设备只能支持语音指令在锁屏之上执行。

不同业务ID的伴随设备关系是独立的，互不干扰，可以独立添加、删除、认证。

当前伴随设备模块的业务有：OH默认业务、锁屏解锁、解锁应用锁以及语音指令在锁屏执行前的身份鉴权等。

业务的添加对于服务端设备支持的场景有要求，如多屏协同业务，要求服务端设备支持委托认证场景。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| ----------- | ---- | ---------- |
| DEFAULT | 0 | 默认业务ID。 |
| VENDOR_BEGIN | 10000 | 厂商自定义业务标识取值起点，实际取值需大于等于10000，避免与系统保留值冲突。 |

## DeviceIdType

设备ID类型。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| ----------------- | ----- | ------------------------------------------------------------ |
| UNIFIED_DEVICE_ID | 1 | 统一设备ID。 |
| VENDOR_BEGIN | 10000 | 厂商自定义业务标识取值起点，实际取值需大于等于10000，避免与系统保留值冲突。 |

## SelectPurpose

选择伴随设备的目的。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| ----------- | ---- | ---------- |
| SELECT_ADD_DEVICE | 1 | 选择用于添加模板的伴随设备。 |
| SELECT_AUTH_DEVICE | 2 | 选择提供认证能力的伴随设备。 |
| VENDOR_BEGIN | 10000 | 厂商自定义业务标识取值起点，实际取值需大于等于10000，避免与系统保留值冲突。 |

## DeviceKey

设备标识。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------------ | ---------- | ---- | ---- | -------------------- |
| deviceIdType | ArkTS-Dyn: number<br />ArkTS-Sta: int | 否 | 否 | 设备ID类型。可以在[DeviceIdType](#deviceidtype)基础上自定义扩展。 |
| deviceId | string | 否 | 否 | 设备ID。 |
| deviceUserId | ArkTS-Dyn: number<br />ArkTS-Sta: int | 否 | 否 | 设备用户ID。 |

## DeviceStatus

设备状态信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------------------- | ------------------------- | ---- | ---- | ---------------------- |
| deviceKey | [DeviceKey](#devicekey) | 否 | 否 | 设备标识信息。 |
| deviceUserName | string | 否 | 否 | 设备用户名。 |
| deviceModelInfo | string | 否 | 否 | 设备模型信息。 |
| deviceName | string | 否 | 否 | 设备名。 |
| isOnline | boolean | 否 | 否 | 设备在线状态，true：设备处于在线状态； false：设备处于离线状态。 |
| supportedBusinessIds | ArkTS-Dyn: number[]<br />ArkTS-Sta: int[] | 否 | 否 | 设备支持的业务ID列表。 |

## TemplateStatus

伴随认证模块维护的模板状态。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------------------ | ------------------------------- | ---- | ---- | -------------------- |
| templateId | Uint8Array | 否 | 否 | 模板ID。 |
| isConfirmed | boolean | 否 | 否 | 数据确认状态，true：数据是实时数据；false：数据是缓存数据。 |
| isValid | boolean | 否 | 否 | 模板是否有效，true：模板有效；false：模板无效。 |
| localUserId | ArkTS-Dyn: number<br />ArkTS-Sta: int | 否 | 否 | 本地用户ID。 |
| addedTime | Date | 否 | 否 | 模板添加时间。格式为Unix时间戳，即自1970年1月1日起经过的毫秒数。 |
| enabledBusinessIds | ArkTS-Dyn: number[]<br />ArkTS-Sta: int[] | 否 | 否 | 支持的业务ID列表。 |
| deviceStatus | [DeviceStatus](#devicestatus) | 否 | 否 | 设备的状态信息。 |

## TemplateStatusCallback

type TemplateStatusCallback = (templateStatusList: TemplateStatus[]) => void

回调函数，用于接收模板状态。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型  | 必填 | 说明 |
| ------------------ | ------------------------------------- | ---- | -------------- |
| templateStatusList | [TemplateStatus](#templatestatus)[] | 是 | 模板状态列表。 |

## ContinuousAuthStatusCallback

type ContinuousAuthStatusCallback = (isAuthPassed: boolean, authTrustLevel?: UserAuth.AuthTrustLevel) => void

回调函数，用于接收持续认证状态。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------------- | ----------------------- | ---- | ------------------------------------------------------------ |
| isAuthPassed | boolean | 是 | 是否通过认证，true：通过认证；false：未通过认证。 |
| authTrustLevel | [UserAuth.AuthTrustLevel](./js-apis-useriam-userauth.md#authtrustlevel8) | 否 | 期望达到的认证可信等级。典型操作需要的身份认证可信等级，具体请参见[认证可信等级划分原则](../../security/UserAuthenticationKit/user-authentication-overview.md#生物认证可信等级划分原则)。 |

## AvailableDeviceStatusCallback

type AvailableDeviceStatusCallback = (deviceStatusList: DeviceStatus[]) => void

回调函数，用于接收可添加的设备列表变化。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---------------- | --------------------------------- | -------------- | -------------- |
| deviceStatusList | [DeviceStatus](#devicestatus)[] | 是 | 设备状态列表。 |

## ContinuousAuthParam

持续认证相关参数。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---------- | ---------- | ---- | ---- | -------------------------------------------- |
| templateId | Uint8Array | 否 | 是 | 模板ID。未填写时默认订阅当前用户下全部模板。 |

## StatusMonitor

用于监听或获取模板或持续认证状态等的对象。

### getTemplateStatus

getTemplateStatus(): Promise&lt;TemplateStatus[]&gt;

获得伴随设备模板状态。使用Promise异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| ------------------------------------- | ------------------------------------------------------ |
| Promise&lt;[TemplateStatus](#templatestatus)[]&gt;| Promise对象，返回全部的模板状态列表。 |

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

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
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

取消订阅伴随设备的持续认证状态。使用callback异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [ContinuousAuthStatusCallback](#continuousauthstatuscallback) | 否 | 指定取消注册的回调函数，若不填此参数，则取消onContinuousAuthChange注册的全部回调。 |

**错误码：**

以下错误码的详细介绍请参见[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------------------------------------------------------------ |
| 32600001 | The system service is not working properly. Please try again later. |

**示例：**

```ts
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
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

ArkTS-Dyn: getStatusMonitor(localUserId: number): StatusMonitor

ArkTS-Sta: getStatusMonitor(localUserId: int): StatusMonitor

获取状态监听器，用于后续查询和订阅伴随模板信息等。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----------- | ---- | ---- | ------------ |
| localUserId | ArkTS-Dyn: number<br />ArkTS-Sta: int | 是 | 本地用户ID。 |

**返回值：**

| 类型 | 说明 |
| --------------------------------- | ------------------------------ |
| [StatusMonitor](#statusmonitor) | 用于查询和订阅伴随模板信息等。 |

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
import { osAccount, BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
try {
  const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
  const continuousAuthParam: companionDeviceAuth.ContinuousAuthParam = {
    templateId: new Uint8Array([])
  };
  const handler = (isAuthPassed: boolean, authTrustLevel?: osAccount.AuthTrustLevel): void => {
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

伴随设备选择回调的返回结果。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---------------- | --------------------------- | ---- | ---- | ------------------------------------------ |
| deviceKeys | [DeviceKey](#devicekey)[] | 否 | 否 | 设备信息列表。|
| selectionContext | Uint8Array | 否 | 是 | 设备选择上下文，携带了json格式的扩展信息。 |

## DeviceSelectCallback

ArkTS-Dyn: type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult

ArkTS-Sta: type DeviceSelectCallback = (selectPurpose: int) => DeviceSelectResult

伴随设备选择回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------- | ---- | ---- | ------------------------------------------------------------ |
| selectPurpose | ArkTS-Dyn: number<br />ArkTS-Sta: int | 是 | 指定选择目的。具体取值参见[SelectPurpose](#selectpurpose)，业务可自定义。 |

**返回值：**

| 类型 | 说明 |
| ------------------------------------------- | -------------------- |
| [DeviceSelectResult](#deviceselectresult) | 返回的设备选择结果。 |

## companionDeviceAuth.registerDeviceSelectCallback

registerDeviceSelectCallback(callback: DeviceSelectCallback): void

用于注册订阅伴随设备选择的回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [DeviceSelectCallback](#deviceselectcallback) | 是 | 伴随设备选择的回调。 |

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

用于取消注册订阅伴随设备选择的回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

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

ArkTS-Dyn: updateEnabledBusinessIds(templateId: Uint8Array, enabledBusinessIds: number[]): Promise&lt;void&gt;

ArkTS-Sta: updateEnabledBusinessIds(templateId: Uint8Array, enabledBusinessIds: int[]): Promise&lt;void&gt;

用于更新指定伴随设备模板支持的业务范围。使用Promise异步回调。

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------------------ | ---------- | ---- | ------------------------ |
| templateId | Uint8Array | 是 | 目标模板ID。 |
| enabledBusinessIds | ArkTS-Dyn: number[]<br />ArkTS-Sta: int[] | 是 | 模板支持的业务ID集合。 |

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
