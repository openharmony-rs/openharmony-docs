# StatusMonitor（系统接口）

状态监听器对象。用于监听或获取模板状态、持续认证状态、可添加设备状态等信息。通过[getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md#getstatusmonitor-1)获取此对象。

**起始版本：** 23

<!--Device-companionDeviceAuth-interface StatusMonitor--><!--Device-companionDeviceAuth-interface StatusMonitor-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

<a id="gettemplatestatus"></a>
## getTemplateStatus

```TypeScript
getTemplateStatus(): Promise<TemplateStatus[]>
```

获取伴随设备模板状态。用于查询当前用户下所有已注册的伴随设备认证模板的状态信息，包括模板有效性、支持的业务范围、关联设备状态等。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-getTemplateStatus(): Promise<TemplateStatus[]>--><!--Device-StatusMonitor-getTemplateStatus(): Promise<TemplateStatus[]>-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TemplateStatus[]&gt; | Promise对象，成功时返回当前用户下全部模板的状态列表，每个模板状态包含模板ID、有效性、设备信息等；失败时抛出相应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

```TypeScript
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

<a id="offavailabledevicechange"></a>
## offAvailableDeviceChange

```TypeScript
offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void
```

取消订阅可添加的伴随设备状态变化，使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void--><!--Device-StatusMonitor-offAvailableDeviceChange(callback?: AvailableDeviceStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | 否 | 需要取消的目标回调。不传入callback时默认移除当前应用注册的全部相关回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

<a id="offcontinuousauthchange"></a>
## offContinuousAuthChange

```TypeScript
offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void
```

取消订阅伴随设备的持续认证状态变化事件。取消后，应用将不再接收持续认证状态变化通知。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void--><!--Device-StatusMonitor-offContinuousAuthChange(callback?: ContinuousAuthStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | 否 | 指定取消注册的回调函数。若传入此参数，仅取消该特定回调的注册；若不传入此参数，则取消onContinuousAuthChange注册的全部回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

<a id="offtemplatechange"></a>
## offTemplateChange

```TypeScript
offTemplateChange(callback?: TemplateStatusCallback): void
```

取消订阅模板的状态变化。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-offTemplateChange(callback?: TemplateStatusCallback): void--><!--Device-StatusMonitor-offTemplateChange(callback?: TemplateStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | 否 | 指定取消注册的回调函数。若不填此参数，则取消onTemplateChange注册的全部回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

<a id="onavailabledevicechange"></a>
## onAvailableDeviceChange

```TypeScript
onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void
```

订阅可添加的伴随设备状态变化。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void--><!--Device-StatusMonitor-onAvailableDeviceChange(callback: AvailableDeviceStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | 是 | 处理可选设备更新的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

<a id="oncontinuousauthchange"></a>
## onContinuousAuthChange

```TypeScript
onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void
```

订阅伴随设备的持续认证状态。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void--><!--Device-StatusMonitor-onContinuousAuthChange(param: ContinuousAuthParam, callback: ContinuousAuthStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ContinuousAuthParam](arkts-userauthentication-companiondeviceauth-continuousauthparam-i-sys.md) | 是 | 用于指定订阅的设备。 |
| callback | [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | 是 | 订阅的设备持续认证状态发生变化时执行此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |
| [32600002](../errorcode-useriam.md#32600002-模板未找到) | The template is not found. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

<a id="ontemplatechange"></a>
## onTemplateChange

```TypeScript
onTemplateChange(callback: TemplateStatusCallback): void
```

订阅模板的状态变化。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StatusMonitor-onTemplateChange(callback: TemplateStatusCallback): void--><!--Device-StatusMonitor-onTemplateChange(callback: TemplateStatusCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | 是 | 回调函数，用于接收模板状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

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
  console.error(`error has been captured: message:${message}`);
}

```

