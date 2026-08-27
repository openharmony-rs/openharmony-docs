# p2pConnect

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## p2pConnect

```TypeScript
function p2pConnect(config: WifiP2PConfig): void
```

使用指定配置发起与设备的P2P连接。

**起始版本：** 10

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiP2PConfig | 是 | 表示连接到指定群组的配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1.Incorrect parameter types. 2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  let recvP2pConnectionChangeFunc = (result:wifiManager.WifiP2pLinkedInfo) => {
      console.info("p2p connection change receive event: " + JSON.stringify(result));
      wifiManager.getP2pLinkedInfo((err, data:wifiManager.WifiP2pLinkedInfo) => {
          if (err) {
              console.error('failed to get getP2pLinkedInfo: ' + JSON.stringify(err));
              return;
          }
          console.info("get getP2pLinkedInfo: " + JSON.stringify(data));
      });
  }
  wifiManager.on("p2pConnectionChange", recvP2pConnectionChangeFunc);
  
  let recvP2pDeviceChangeFunc = (result:wifiManager.WifiP2pDevice) => {
      console.info("p2p device change receive event: " + JSON.stringify(result));
  }
  wifiManager.on("p2pDeviceChange", recvP2pDeviceChangeFunc);
  
  let recvP2pPeerDeviceChangeFunc = (result:wifiManager.WifiP2pDevice[]) => {
      console.info("p2p peer device change receive event: " + JSON.stringify(result));
      wifiManager.getP2pPeerDevices((err, data:wifiManager.WifiP2pDevice[]) => {
          if (err) {
              console.error('failed to get peer devices: ' + JSON.stringify(err));
              return;
          }
          console.info("get peer devices: " + JSON.stringify(data));
          let len = data.length;
          for (let i = 0; i < len; ++i) {
              if (data[i].deviceName === "my_test_device") {
                  console.info("p2p connect to test device: " + data[i].deviceAddress);
                  let config:wifiManager.WifiP2PConfig = {
                      deviceAddress:data[i].deviceAddress,
                      netId:-2,
                      passphrase:"",
                      groupName:"",
                      goBand:0,
                  }
                  wifiManager.p2pConnect(config);
              }
          }
      });
  }
  wifiManager.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
  
  let recvP2pPersistentGroupChangeFunc = () => {
      console.info("p2p persistent group change receive event");
  
      wifiManager.getCurrentGroup((err, data:wifiManager.WifiP2pGroupInfo) => {
          if (err) {
              console.error('failed to get current group: ' + JSON.stringify(err));
              return;
          }
          console.info("get current group: " + JSON.stringify(data));
      });
  }
  wifiManager.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
  
  setTimeout(() => {wifiManager.off("p2pConnectionChange", recvP2pConnectionChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pDeviceChange", recvP2pDeviceChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);}, 125 * 1000);
  setTimeout(() =>  {wifiManager.off("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);}, 125 * 1000);
  console.info("start discover devices -> " + wifiManager.startDiscoverDevices());
```
