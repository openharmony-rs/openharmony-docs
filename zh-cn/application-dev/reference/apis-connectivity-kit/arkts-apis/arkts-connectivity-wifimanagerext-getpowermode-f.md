# getPowerMode

## 导入模块

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getPowerMode

```TypeScript
function getPowerMode(): Promise<PowerMode>
```

获取功率模式。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt; |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap扩展模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

async function getWifiPowerMode() {
  try {
    // 1. 使用 await 等待 Promise 解析完成
    let model = await wifiManagerExt.getPowerMode();
    
    console.info("model info: " + model);
  } catch (error) {
    // 2. 捕获 Promise 拒绝时的错误
    console.error("failed: " + JSON.stringify(error));
  }
}
```


## getPowerMode

```TypeScript
function getPowerMode(callback: AsyncCallback<PowerMode>): void
```

获取功率模式。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)&gt; | 是 | 回调函数。当操作成功时，err为0，data表示功率模式。如果err为非0，表示处理出现错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap扩展模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

  wifiManagerExt.getPowerMode((err, data:wifiManagerExt.PowerMode) => {
      if (err) {
          console.error("Failed to get linked information");
          return;
      }
      console.info("get power mode info: " + JSON.stringify(data));
  });

  wifiManagerExt.getPowerMode().then(data => {
      console.info("get power mode info: " + JSON.stringify(data));
  }).catch((error:number) => {
      console.error("get power mode error");
  });
```
