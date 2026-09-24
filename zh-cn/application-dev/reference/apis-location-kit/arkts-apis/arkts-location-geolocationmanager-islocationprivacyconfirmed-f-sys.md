# isLocationPrivacyConfirmed（系统接口）

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isLocationPrivacyConfirmed

```TypeScript
function isLocationPrivacyConfirmed(type: LocationPrivacyType): boolean
```

查询用户是否同意定位服务隐私申明，是否同意启用定位服务。只有系统应用才能调用。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [LocationPrivacyType](arkts-location-geolocation-locationprivacytype-e.md) | 是 | 指定隐私申明场景，例如开机向导中的隐私申明、开启网络定位功能时弹出的隐私申明等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：用户同意定位服务隐私申明。false：用户不同意定位服务隐私申明。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Failed to call ${geoLocationManager.isLocationPrivacyConfirmed} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isConfirmed = geoLocationManager.isLocationPrivacyConfirmed(1);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
