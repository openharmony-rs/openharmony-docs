# getCountryCode

## 导入模块

```TypeScript
```

## getCountryCode

```TypeScript
function getCountryCode(callback: AsyncCallback<CountryCode>): void
```

查询当前的国家码。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CountryCode](arkts-location-geolocationmanager-countrycode-i.md)&gt; | 是 | 回调函数，返回国家码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCountryCode} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301500](../errorcode-geoLocationManager.md#3301500-区域信息包含国家码查询失败) | Failed to query the area information. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.getCountryCode((err, result) => {
    if (err) {
      console.error('getCountryCode: err=' + JSON.stringify(err));
    }
    if (result) {
      console.info('getCountryCode: result=' + JSON.stringify(result));
    }
  });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## getCountryCode

```TypeScript
function getCountryCode(): Promise<CountryCode>
```

查询当前的国家码。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CountryCode](arkts-location-geolocationmanager-countrycode-i.md)&gt; | Promise对象，返回国家码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getCountryCode} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301500](../errorcode-geoLocationManager.md#3301500-区域信息包含国家码查询失败) | Failed to query the area information. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  geoLocationManager.getCountryCode()
    .then((result) => {
      console.info('promise, getCountryCode: result=' + JSON.stringify(result));
    })
    .catch((error: BusinessError) => {
      console.error('promise, getCountryCode: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
