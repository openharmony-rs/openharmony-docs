# STA Development

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=10a823f5114708793f873c2259ddf0b8d1e5f84e translatedAt=2026-10-31T01:19:45.493Z pushedAt=2026-10-31T02:03:16.766Z nl=2 -->

## Introduction
The Wi-Fi STA mode (that is, station mode) enables wireless devices to connect to a wireless local area network (WLAN) as clients. In this mode, devices such as mobile phones, computers, and tablets can access the network by connecting to an access point (AP) or wireless router.


## Use Cases

- [Checking the Wi-Fi Status](#checking-the-wi-fi-status)
- [Establishing a Wi-Fi Connection](#establishing-a-wi-fi-connection)

## Available APIs

For the complete JS API reference and sample code, see [@ohos.wifiManager (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifiManager.md).

The following table describes the related APIs.

| API| Description|
| -------- | -------- |
| isWifiActive() | Checks whether WLAN is enabled.|
| addCandidateConfig() | Adds candidate network configurations. Enable WLAN before using this API.|
| connectToCandidateConfig() | Connects to a candidate network.|
| isConnected() | Checks whether WLAN is connected.|
| removeCandidateConfig() | Removes candidate network configurations.|
| getCandidateConfigs() | Obtains candidate network configurations.|
| on(type: 'wifiStateChange') | Subscribes to WLAN state changes.|
| off(type: 'wifiStateChange') | Unsubscribes from WLAN state changes.|
| on(type: 'wifiConnectionChange') | Subscribes to WLAN connection state changes.|
| off(type: 'wifiConnectionChange') | Unsubscribes from WLAN connection state changes.|


## How to Develop

### Checking the Wi-Fi Status
1. Import the required Wi-Fi module.
2. Check that the **SystemCapability.Communication.WiFi.STA** capability is available.
3. Apply for the **ohos.permission.GET_WIFI_INFO** permission.
4. Enable Wi-Fi on the device.
5. Sample code:

   ```ts
   import { wifiManager } from '@kit.ConnectivityKit';

   let recvPowerNotifyFunc: (result: number) => void = (result: number) => {
     let wifiState = "";
     switch (result) {
       case 0:
         wifiState += 'DISABLED';
         break;
       case 1:
         wifiState += 'ENABLED';
         break;
       case 2:
         wifiState += 'ENABLING';
         break;
       case 3:
         wifiState += 'DISABLING';
         break;
       default:
         wifiState += 'UNKNOWN STATUS';
         break;
     }
     console.info(`Wi-Fi state changed: ${wifiState}`);
   };
   try {
     wifiManager.on("wifiStateChange", recvPowerNotifyFunc);
     let isWifiActive = wifiManager.isWifiActive();
     if (!isWifiActive) {
       console.info("Wi-Fi not enabled. Skipping monitor.");
     } else {
       console.info("Wi-Fi is enabled. Starting monitor...");
     }
   } catch (error) {
     console.error(`WiFi state monitor failed: ${error.message}`);
   } finally {
     try {
       wifiManager.off("wifiStateChange", recvPowerNotifyFunc);
       console.info("Wi-Fi monitor off: listener removed.");
     } catch (e) {
        console.error(`WiFi state monitor failed. ${e.message}`);
     }
   }
   ```

### Establishing a Wi-Fi Connection
1. Import the required Wi-Fi module.
2. Enable Wi-Fi on the device.
3. Check that the **SystemCapability.Communication.WiFi.STA** capability is available.
4. Apply for the **ohos.permission.GET_WIFI_INFO** and **ohos.permission.SET_WIFI_INFO** permissions.
5. Sample code:

   ```ts
   import { wifiManager } from '@kit.ConnectivityKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let recvWifiConnectionChangeFunc = (result: number) => {
     console.info("Receive wifi connection change event: " + result);
     if (result === 1) {
       // A result of 1 indicates that the device is connected. Only then is it meaningful to query the connection status and connection information.
       if (!wifiManager.isConnected()) {
         console.info("Wi-Fi not connected");
       }
       // Obtain the connection information.
       wifiManager.getLinkedInfo().then(data => {
         console.info("get Wi-Fi linked info: " + JSON.stringify(data));
       }).catch((e: BusinessError) => {
         console.error(`getLinkedInfo failed. Code: ${e.code}, message: ${e.message}`);
       });
     }
   }

   try {
     let config: wifiManager.WifiDeviceConfig = {
       ssid: "****",
       bssid: "****",
       preSharedKey: "****",
       securityType: 3 // 3 indicates WIFI_SEC_TYPE_PSK.
     }

     // Update the current Wi-Fi connection status.
     wifiManager.on("wifiConnectionChange", recvWifiConnectionChangeFunc);
     // Add candidate network configurations.
     wifiManager.addCandidateConfig(config).then(result => {
       // Connect to the specified network.
       wifiManager.connectToCandidateConfig(result);
     }).catch((e: BusinessError) => {
       console.error(`addCandidateConfig failed. Code: ${e.code}, message: ${e.message}`);
       // If adding fails, no connection event is generated. Unregister the listener here to avoid leakage.
       try {
         wifiManager.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
       } catch (err) {
         console.error(`off failed. ${err.message}`);
       }
     });
     // Query the signal strength.
     let rssi = -88;
     let band = 1;
     let level = wifiManager.getSignalLevel(rssi, band);
     console.info("level:" + JSON.stringify(level));
   } catch (error) {
     console.error(`WiFi Connection failed. ${error.message}`);
     try {
       wifiManager.off("wifiConnectionChange", recvWifiConnectionChangeFunc);
     } catch (e) {
       console.error(`WiFi Connection off failed. ${e.message}`);
     }
   }
   ```
6. Check the Wi-Fi connection status. For details, see [ConnState](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#connstate).
7. For details about error codes, see [Wi-Fi Error Codes](../../reference/apis-connectivity-kit/errorcode-wifi.md).
