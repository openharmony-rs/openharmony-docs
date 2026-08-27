# createGroup

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## createGroup

```TypeScript
function createGroup(config: WifiP2PConfig): boolean
```

创建P2P群组。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** createP2pGroup

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiP2PConfig | 是 | 创建群组的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let config:wifi.WifiP2PConfig = {
    deviceAddress: "****",
    netId: 0,
    passphrase: "*****",
    groupName: "****",
    goBand: 0
  }
  wifi.createGroup(config);  
  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
