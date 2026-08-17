# stopDiscoverDevices

## stopDiscoverDevices

```TypeScript
function stopDiscoverDevices(): boolean
```

停止发现WLAN P2P设备。

**起始版本：** 8

**ArkTS模式：** 起始版本为8。

**废弃版本：** 9

**替代接口：** stopDiscoverP2pDevices

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function stopDiscoverDevices(): boolean--><!--Device-wifi-function stopDiscoverDevices(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

## 示例

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.stopDiscoverDevices();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

