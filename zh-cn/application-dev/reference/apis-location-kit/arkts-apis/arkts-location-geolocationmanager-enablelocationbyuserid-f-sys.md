# enableLocationByUserId（系统接口）

## 导入模块

```TypeScript
```

## enableLocationByUserId

```TypeScript
function enableLocationByUserId(userId: number): Promise<void>
```

打开指定系统账号的定位开关，使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.enableLocationByUserId} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 打开指定系统账号的位置开关，如：处于ID为101的账号下，可以打开ID为100的账号的位置开关
  let userId: number = 100;
  geoLocationManager.enableLocationByUserId(userId).then(() => {
    console.info('promise, enableLocationByUserId succeed');
  })
    .catch((error: BusinessError) => {
      console.error('promise, enableLocationByUserId: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
