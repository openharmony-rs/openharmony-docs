# StatusMonitor（系统接口）

状态监听器对象。用于监听或获取模板状态、持续认证状态、可添加设备状态等信息。通过[getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md)获取此对象。

**起始版本：** 23

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## getTemplateStatus

```TypeScript
getTemplateStatus(): Promise<TemplateStatus[]>
```

获取伴随设备模板状态。用于查询当前用户下所有已注册的伴随设备认证模板的状态信息，包括模板有效性、支持的业务范围、关联设备状态等。使用Promise异步回调。

数据来源：返回系统服务（UserIAM）维护的模板状态内存快照，非实时跨设备查询。

与onTemplateChange的区别：getTemplateStatus用于一次性获取当前模板状态快照，适合主动查询；onTemplateChange用于持续订阅模板状态变化，适合实时响应。仅需获取一次状态时使用getTemplateStatus，需要持续监听变化时使用onTemplateChange。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TemplateStatus](arkts-userauthentication-companiondeviceauth-templatestatus-i-sys.md)[]&gt; | Promise对象，成功时返回当前用户下全部模板的状态列表，每个模板状态包含模板ID、有效性、设备信息等；失败时抛出相应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const localUserId = 100;
const statusMonitor = companionDeviceAuth.getStatusMonitor(localUserId);
statusMonitor.getTemplateStatus()
  .then((templateStatus) => {
    console.info(`templateStatus: ${JSON.stringify(templateStatus)}`);
  })
  .catch((error: BusinessError) => {
    console.error(`error has been captured. Code: ${error.code}, message: ${error.message}`);
  })
```

## offAvailableDeviceChange

```TypeScript
offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void
```

取消订阅可添加的伴随设备状态变化。callback参数用于指定要取消的回调函数，不传入则取消全部已注册的回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | 否 | 此前通过onAvailableDeviceChange注册的回调函数。指定该参数时，仅取消指定的这一个回调；省略该参数时，取消全部已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```

## offContinuousAuthChange

```TypeScript
offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void
```

取消订阅伴随设备的持续认证状态变化事件。取消后，应用将不再接收持续认证状态变化通知。callback参数用于指定要取消的回调函数，不传入则取消全部已注册的回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | 否 | 此前通过onContinuousAuthChange注册的回调函数。指定该参数时，仅取消指定的这一个回调；省略该参数时，取消全部已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```

## offTemplateChange

```TypeScript
offTemplateChange(callback?: TemplateStatusCallback): void
```

取消订阅模板的状态变化。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | 否 | 回调函数，指定该参数时，仅取消指定的这一个回调；省略该参数时，取消全部已注册的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```

## onAvailableDeviceChange

```TypeScript
onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void
```

订阅可添加的伴随设备状态变化。使用callback异步回调。

触发机制：当可添加的伴随设备列表发生变化（如新设备上线、设备离线、设备绑定关系变化等）时触发回调。订阅时立即推送一次当前列表。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | 是 | 处理可用设备状态变化的回调函数。当可添加设备列表变化（如新设备上线、设备离线等）时触发，回调参数为设备状态列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```

## onContinuousAuthChange

```TypeScript
onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void
```

订阅伴随设备的持续认证状态。使用callback异步回调。

持续认证：持续认证状态指伴随设备是否持有有效认证令牌。当令牌签发（认证通过）、令牌超时、关联设备离线或令牌被吊销时状态发生变化并触发回调。authTrustLevel为当前有效令牌中的最高认证可信等级。仅当认证可信等级变化时通知；订阅时立即推送一次当前状态。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ContinuousAuthParam](arkts-userauthentication-companiondeviceauth-continuousauthparam-i-sys.md) | 是 | 用于指定订阅参数，可通过templateId字段指定目标模板。 |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | 是 | 回调函数。当持续认证状态变化时触发，回调参数为认证结果（isAuthPassed）和认证可信等级（authTrustLevel）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |
| [32600002](../errorcode-useriam.md#32600002-模板未找到) | The template is not found. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```

## onTemplateChange

```TypeScript
onTemplateChange(callback: TemplateStatusCallback): void
```

订阅模板的状态变化。使用callback异步回调。

触发时机：模板状态变化时触发，包括启用业务ID变更、有效性变更、关联设备上下线/状态变更、模板加入或移除IDM等。订阅时立即推送一次当前状态快照；状态未变化时不重复通知。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | 是 | 回调函数。当模板状态发生变化（如添加、删除、有效性变更等）时触发，回调参数为模板状态列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例**

```TypeScript
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
  console.error(`error has been captured. Code: ${(error as BusinessError).code}, message: ${message}`);
}
```
