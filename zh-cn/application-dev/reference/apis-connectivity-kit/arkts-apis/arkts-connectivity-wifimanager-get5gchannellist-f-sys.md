# get5GChannelList（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## get5GChannelList

```TypeScript
function get5GChannelList(): Array<int>
```

获取设备支持的5G信道列表。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifiManager-function get5GChannelList(): Array<int>--><!--Device-wifiManager-function get5GChannelList(): Array<int>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 返回5G信道列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let channelList = wifiManager.get5GChannelList();
  console.info("channelList:" + JSON.stringify(channelList));    
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

