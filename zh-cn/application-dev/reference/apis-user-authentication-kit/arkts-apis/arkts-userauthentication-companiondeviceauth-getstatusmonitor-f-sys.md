# getStatusMonitor（系统接口）

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## getStatusMonitor

```TypeScript
function getStatusMonitor(localUserId: number): StatusMonitor
```

获取状态监听器。用于获取指定用户的状态监听器对象，通过该对象可查询和订阅伴随设备的模板状态、持续认证状态、可添加设备状态等信息。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-function getStatusMonitor(localUserId: int): StatusMonitor--><!--Device-companionDeviceAuth-function getStatusMonitor(localUserId: int): StatusMonitor-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localUserId | number | 是 | 本地用户ID。主设备上的用户标识，为大于等于0的正整数。用于获取该用户对应的伴随设备状态监听器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StatusMonitor](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md) | 状态监听器对象。可用于查询模板状态（[getTemplateStatus](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#gettemplatestatus-1)）、订阅模板变化（[onTemplateChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#ontemplatechange-1)）、订阅可添加设备变化（[onAvailableDeviceChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#onavailabledevicechange-1)）、订阅持续认证状态（[onContinuousAuthChange](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md#oncontinuousauthchange-1)）等操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |
| [32600002](../errorcode-useriam.md#32600002-模板未找到) | The local user is not found. |

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

