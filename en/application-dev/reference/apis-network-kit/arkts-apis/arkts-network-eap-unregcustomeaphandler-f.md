# unregCustomEapHandler

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## unregCustomEapHandler

```TypeScript
function unregCustomEapHandler(netType:number, eapCode: number, eapType: number, callback: Callback<EapData>): void
```

Unregisters the custom handler of EAP packets for extensible authentication. This API returns the result asynchronously through a callback.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netType | number | Yes | Network type. The value can be **1** or **2**.<br>The value **1** indicates WLAN, and the value **2** indicates Ethernet. |
| eapCode | number | Yes | EAP code. The value can be any of the following:<br>code=1 Request, code=2 Response, code=3 Success, code=4 Failure. |
| eapType | number | Yes | EAP method. The value range is [0, 255].<br>Common values include the following: eapType=1 Identity, eapType=2 Notification, eapType=3 NAK, eapType=4 MD5-Challenge, eapType=5 OTP (One-Time Password), eapType=6 GTC (Generic Token Card), eapType=13 EAP-TLS, eapType=21 EAP-TTLS, eapType=25 EAP-PEAP, eapType=254 Expanded Types, and eapType=255 Experimental use. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EapData](arkts-network-eap-eapdata-i.md)&gt; | Yes | Callback function, which returns the packet of the specified eapCode+ eapType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [33200006](../errorcode-net-eap.md#33200006-invalid-network-type) | Invalid net type |
| [33200007](../errorcode-net-eap.md#33200007-invalid-eapcode-value) | Invalid eap code |
| [33200008](../errorcode-net-eap.md#33200008-invalid-eaptype-value) | Invalid eap type |
| [33200009](../errorcode-net-eap.md#33200009-netmanager-not-exist) | netmanager stop |
| [33200099](../errorcode-net-eap.md#33200099-internal-program-error) | internal error |

**Examples**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netType = 1;
let eapCode = 1;
let eapType = 25;
let eapData = (eapData:eap.EapData):void => {
  console.info("rsp result", JSON.stringify(eapData));
};
    
eap.unregCustomEapHandler(netType, eapCode, eapType, eapData);
console.info('unregCustomEapHandler success');
```
