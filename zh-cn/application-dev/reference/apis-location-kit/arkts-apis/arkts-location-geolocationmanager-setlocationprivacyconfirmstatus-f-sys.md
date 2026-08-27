# setLocationPrivacyConfirmStatus（系统接口）

## 导入模块

```TypeScript
```

## setLocationPrivacyConfirmStatus

```TypeScript
function setLocationPrivacyConfirmStatus(type: LocationPrivacyType, isConfirmed: boolean): void
```

设置用户勾选定位服务隐私申明的状态，记录用户是否同意启用定位服务。只有系统应用才能调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_SECURE_SETTINGS

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | LocationPrivacyType | 是 | 指定隐私申明场景，例如开机向导中的隐私申明、开启网络定位功能时弹出的隐私申明等。 |
| isConfirmed | boolean | 是 | true：用户同意定位服务隐私申明。 false：用户不同意定位服务隐私申明。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.setLocationPrivacyConfirmStatus} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.setLocationPrivacyConfirmStatus(1, true);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
