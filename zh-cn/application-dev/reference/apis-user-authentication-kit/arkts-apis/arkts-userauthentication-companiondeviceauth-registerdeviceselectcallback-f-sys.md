# registerDeviceSelectCallback（系统接口）

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

<a id="registerdeviceselectcallback"></a>
## registerDeviceSelectCallback

```TypeScript
function registerDeviceSelectCallback(callback: DeviceSelectCallback): void
```

注册伴随设备选择回调。当系统需要用户选择伴随设备时，会调用此回调，应用需在回调中返回用户选择的设备信息。通过此回调，应用可以实现自定义的设备选择逻辑，如弹出设备选择界面让用户选择。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-companionDeviceAuth-function registerDeviceSelectCallback(callback: DeviceSelectCallback): void--><!--Device-companionDeviceAuth-function registerDeviceSelectCallback(callback: DeviceSelectCallback): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DeviceSelectCallback](arkts-userauthentication-companiondeviceauth-deviceselectcallback-t-sys.md) | 是 | 伴随设备选择回调函数。系统调用时会传入选择目的（selectPurpose），应用需根据目的返回相应的DeviceSelectResult，包含用户选择的设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [32600001](../errorcode-useriam.md#32600001-系统服务工作异常) | The system service is not working properly. Please try again later. |

**示例：**

```TypeScript
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

