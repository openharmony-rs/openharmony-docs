# P2P Connection Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
## Introduction
The peer-to-peer (P2P) mode provides a point-to-point connection between devices in a WLAN. It enables the direct establishment of a TCP/IP connection between two stations (STAs) without the involvement of an access point (AP).

## When to Use
You can use the APIs provided by the **wifiManager** module to:

- Create or remove a P2P group.
- Set up a P2P connection.

## Available APIs

For details about the JavaScript APIs and sample code, see the [P2P API Reference](../../reference/apis-connectivity-kit/js-apis-wifiManager.md).

The following table describes the APIs used in this topic.

| API| Description|
| -------- | -------- |
| createGroup() | Creates a P2P group.|
| removeGroup() | Removes a P2P group.|
| startDiscoverDevices()  | Starts to discover devices.|
| getP2pPeerDevices() | Obtains the P2P peer device list.|
| p2pConnect() | Sets up a P2P connection.|
| getP2pLinkedInfo() | Obtains P2P connection information.|
| on(type: 'p2pPersistentGroupChange') | Subscribes to P2P persistent group state changes.|
| off(type: 'p2pPersistentGroupChange') | Unsubscribes from P2P persistent group state changes.|
| on(type: 'p2pPeerDeviceChange') | Subscribes to P2P peer device state changes.|
| off(type: 'p2pPeerDeviceChange') | Unsubscribes from P2P peer device state changes.|
| on(type: 'p2pConnectionChange') | Subscribes to P2P connection state changes.|
| off(type: 'p2pConnectionChange') | Unsubscribes from P2P connection state changes.|

## How to Develop

### Creating or Removing a P2P Group
1. Import the Wi-Fi module.
<!-- @[wifiManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/Wlan/entry/src/main/ets/pages/P2pSetting.ets) -->

``` TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```
2. Enable Wi-Fi on the device.
3. Check that the device has the SystemCapability.Communication.WiFi.P2P capability.
4. Create or remove a P2P group.
<!-- @[createGrop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/Wlan/entry/src/main/ets/pages/P2pSetting.ets) -->

``` TypeScript
async createGroup() {
  try {
    let deviceInfo = await wifiManager.getP2pLocalDevice()
    let config:wifiManager.WifiP2PConfig = {
      deviceAddress: deviceInfo.deviceAddress,
      netId: this.netId,
      passphrase: this.passphrase,
      groupName: this.groupName,
      goBand: this.goBand,
    }
    hilog.info(`deviceAddress: ${config.deviceAddress}, netId: ${config.netId}, pwd: ${config.passphrase}, gpname: ${config.groupName}, goBand: ${config.goBand}`)
    wifiManager.createGroup(config)
    promptAction.showToast({ message : 'createGroup success' })
  } catch (e) {
    hilog.info(TAG, `createGroup Error: ${JSON.stringify(e)}`)
  }
}
```
5. Example:

   ```ts
   import { wifiManager } from '@kit.ConnectivityKit';

   // Create a P2P group. To use the current device as the group owner (GO), set:
   // netId: The value -1 means to create a temporary P2P group. When a device in the group is to be connected next time, GO negotiation and WPS key negotiation must be performed again.
   // The value -2 means to create a persistent group. The device in the group can be reconnected without GO negotiation or WPS key negotiation.

   let recvP2pPersistentGroupChangeFunc = () => {
     console.info("p2p persistent group change receive event");

     // Services to be processed after the persistent group is created.
   }
   // Create a persistent group, and register a listener callback for the persistent group status changes.
   wifiManager.on("p2pPersistentGroupChange", recvP2pPersistentGroupChangeFunc);
   try {
     let config: wifiManager.WifiP2PConfig = {
       deviceAddress: "00:11:22:33:44:55",
       deviceAddressType: 1,
       netId: -2,
       passphrase: "12345678",
       groupName: "testGroup",
       goBand: 0
   }
     wifiManager.createGroup(config);
   } catch (error) {
     console.error("failed:" + JSON.stringify(error));
   }

   // Remove a P2P group.
   try {
     wifiManager.removeGroup();
   } catch (error) {
     console.error("failed:" + JSON.stringify(error));
   }
   ```

6. For details about error codes, see [Wi-Fi Error Codes](../../reference/apis-connectivity-kit/errorcode-wifi.md).

### Setting Up a P2P Connection
1. Import the Wi-Fi module.
<!-- @[wifiManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/Wlan/entry/src/main/ets/pages/P2pSetting.ets) -->

``` TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```
2. Enable Wi-Fi on the device.
3. Check that the device has the SystemCapability.Communication.WiFi.P2P capability.
4. Register a callback for **p2pPeerDeviceChange** and set up a P2P connection in the callback implementation.
<!-- @[connectP2p](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/Wlan/entry/src/main/ets/pages/AvailableP2p.ets) -->

``` TypeScript
connectP2p(p2pScanInfo: wifi.WifiP2pDevice) {
  promptAction.showToast({ message : 'connect to device' })
  hilog.info(TAG , `connect deviceAddress=${ p2pScanInfo.deviceAddress }`)
  hilog.info(TAG , `p2pScanInfo:` + JSON.stringify(p2pScanInfo))
  let config: wifi.WifiP2PConfig = {
    deviceAddress : p2pScanInfo.deviceAddress,
    netId : - 2 ,
    deviceAddressType: 1,
    passphrase : '' ,
    groupName : '' ,
    goBand : 0
  }
  wifi.p2pConnect(config)
}
```
5. Start P2P device discovery.
<!-- @[discover_p2p_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ConnectivityKit/Wlan/entry/src/main/ets/pages/AvailableP2p.ets) -->

``` TypeScript
aboutToAppear() {
  // If Wi-Fi is enabled, record the status. Then, scan for P2P devices and obtain the connection information.
  if (!wifi.isWifiActive()) {
    promptAction.showToast({ message : 'place active wifi' })
    return
  }
  this.isSwitchOn = true;
  wifi.startDiscoverDevices()
  this.addListener();
}

aboutToDisappear() {
  wifi.off('p2pPeerDeviceChange')
  wifi.off('p2pConnectionChange')
}
```
6. Example:

   ```ts
   import { wifiManager } from '@kit.ConnectivityKit';

   let recvP2pConnectionChangeFunc = (result: wifiManager.WifiP2pLinkedInfo) => {
     console.info("p2p connection change receive event: " + JSON.stringify(result));
     wifiManager.getP2pLinkedInfo((err, data) => {
       if (err) {
         console.error("failed to get P2pLinkedInfo: " + JSON.stringify(err));
         return;
       }
       console.info("get getP2pLinkedInfo: " + JSON.stringify(data));
       // Add the service processing logic after a successful or failed P2P connection.
     });
   }
   // After the P2P connection is set up, the callback for p2pConnectionChange will be called.
   wifiManager.on("p2pConnectionChange", recvP2pConnectionChangeFunc);

   let recvP2pPeerDeviceChangeFunc = (result: wifiManager.WifiP2pDevice[]) => {
     console.info("p2p peer device change receive event: " + JSON.stringify(result));
     wifiManager.getP2pPeerDevices((err, data) => {
       if (err) {
         console.error("failed to get peer devices: " + JSON.stringify(err));
         return;
       }
       console.info("get peer devices: " + JSON.stringify(data));
       let len = data.length;
       for (let i = 0; i < len; ++i) {
         // Select the peer device that meets the conditions.
         if (data[i].deviceName === "my_test_device") {
           console.info("p2p connect to test device: " + data[i].deviceAddress);
           let config: wifiManager.WifiP2PConfig = {
             deviceAddress: data[i].deviceAddress,
             deviceAddressType: 1,
             netId: -2,
             passphrase: "",
             groupName: "",
             goBand: 0,
           }
           // Set up a P2P connection. The GO cannot initiate connections.
           wifiManager.p2pConnect(config);
         }
       }
     });
   }
   // The callback for p2pPeerDeviceChange will be called when the P2P scanning result is reported.
   wifiManager.on("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);

   setTimeout(() => {
     wifiManager.off("p2pConnectionChange", recvP2pConnectionChangeFunc);
   }, 125 * 1000);
   setTimeout(() => {
     wifiManager.off("p2pPeerDeviceChange", recvP2pPeerDeviceChangeFunc);
   }, 125 * 1000);
   // Start to discover P2P devices, that is, start P2P scanning.
   console.info("start discover devices -> " + wifiManager.startDiscoverDevices());
   ```

7. For details about error codes, see [Wi-Fi Error Codes](../../reference/apis-connectivity-kit/errorcode-wifi.md).

### Obtaining the IP Address of the Peer Device and Performing Socket Communication
1. Import the Wi-Fi module.
2. Enable Wi-Fi on the device.
3. Check that the device has the SystemCapability.Communication.WiFi.P2P capability.
4. Call [wifiP2pLinkedInfo.connectState](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#p2pconnectstate9) to check whether the P2P connection status is **CONNECTED**.
5. Call [wifiP2pGroupInfo.goIpAddress](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifip2pgroupinfo9) to obtain the P2P group IP address for socket communication.
6. Perform socket communication. For details, see [Using Socket for Network Access](../../../application-dev/network/socket-connection.md).
