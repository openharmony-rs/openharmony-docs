# p2pCancelConnect

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## p2pCancelConnect

```TypeScript
function p2pCancelConnect(): boolean
```

取消P2P连接。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.p2pCancelConnect();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
