# @ohos.net.eap (Extensible Authentication)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @foredward-->
<!--Designer: @gcw_3Lx1FoMT-->
<!--Tester: @WIFIroam-test-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3a04f0d1af5fda4a2c90d98830e36cd7dbd8f4cf translatedAt=2026-11-04T06:40:52.188Z pushedAt=2026-11-04T08:04:44.886Z nl=1 -->

This module provides a mechanism for third-party clients to access the 802.1X authentication (a port-based network access control protocol) process, supporting functions such as customized authentication for clients. It also provides Ethernet 802.1X EAP configuration management, authentication control, and authentication status listening.

> **NOTE** 
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Module to Import

```js
import {eap} from '@kit.NetworkKit';
```

## eap.regCustomEapHandler

regCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData\>): void

Registers a custom handler of Extensible Authentication Protocol (EAP) packets for extensible authentication. This API returns the result asynchronously through a callback.

The system will encapsulate the eligible EAP packets into the callback function for enterprise applications to retrieve.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                             | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| netType| number|Yes|Network type. The value is 1 or 2.<br>netType=1 indicates WLAN (WLAN is supported only on PC/2-in-1 devices), and netType=2 indicates Ethernet.|
| eapCode|number |Yes|EAP code. The value can be any of the following:<br>code=1 Request, code=2 Response, code=3 Success, code=4 Failure.|
| eapType| number |Yes|EAP method. The value range is [0, 255].<br>Common values include the following: eapType=1 Identity, eapType=2 Notification, eapType=3 NAK, eapType=4 MD5-Challenge, eapType=5 OTP (One-Time Password), eapType=6 GTC (Generic Token Card), eapType=13 EAP-TLS, eapType=21 EAP-TTLS, eapType=25 EAP-PEAP, eapType=254 Expanded Types, and eapType=255 Experimental use.|
| callback| Callback\<[EapData](#eapdata)\> |Yes|Callback function, which returns the packet of the specified eapCode+eapType.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Extensible Authentication Error Codes](errorcode-net-eap.md).

| Error Code| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.          |
|33200006 | Invalid net type.          |
|33200007 | Invalid eap code.          |
|33200008 | Invalid eap type.          |
|33200009 | netmanager stop.          |
|33200099 | internal error.          |

**Example**

```js
import {eap} from '@kit.NetworkKit';
let netType = 1;
let eapCode = 1;
let eapType = 25;
let eapData = (eapData:eap.EapData):void => {
  console.info("rsp result", JSON.stringify(eapData));
};

eap.regCustomEapHandler(netType, eapCode, eapType, eapData);
console.info('regCustomEapHandler success');
```

## eap.unregCustomEapHandler

unregCustomEapHandler(netType:number, eapCode: number, eapType: number, callback: Callback\<EapData\>): void

Unregisters the custom handler of EAP packets for extensible authentication. This API returns the result asynchronously through a callback.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                           | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| netType| number|Yes|Network type. The value is 1 or 2.<br>netType=1 indicates WLAN (WLAN is supported only on PC/2-in-1 devices), and netType=2 indicates Ethernet.|
| eapCode|number |Yes|EAP code. The value can be any of the following:<br>code=1 Request, code=2 Response, code=3 Success, code=4 Failure.|
| eapType| number |Yes|EAP method. The value range is [0, 255].<br>Common values include the following: eapType=1 Identity, eapType=2 Notification, eapType=3 NAK, eapType=4 MD5-Challenge, eapType=5 OTP (One-Time Password), eapType=6 GTC (Generic Token Card), eapType=13 EAP-TLS, eapType=21 EAP-TTLS, eapType=25 EAP-PEAP, eapType=254 Expanded Types, and eapType=255 Experimental use.|
| callback| Callback\<[EapData](#eapdata)\> |Yes|Callback function, which returns the packet of the specified eapCode+eapType.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Extensible Authentication Error Codes](errorcode-net-eap.md).

| Error Code| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.          |
|33200006 | Invalid net type.          |
|33200007 | Invalid eap code.          |
|33200008 | Invalid eap type.          |
|33200009 | netmanager stop.          |
|33200099 | internal error.          |

**Example**

```js
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

## eap.replyCustomEapData

replyCustomEapData(result: CustomResult, data: EapData): void

Notifies the system of the extensible authentication result.

 > **NOTE**
 >
 >- If this callback is used to process received EAP data packets, the customized portion added by the server must be removed from the EAP data transmitted to the system.
 >- If this callback is used to process sent EAP data packets, the EAP data transmitted to the system is the EAP data with the customized portion added by the server.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                           | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| result | [CustomResult](#customresult)|Yes|Extensible authentication result.|
| data | [EapData](#eapdata) |Yes|EAP data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Extensible Authentication Error Codes](errorcode-net-eap.md).

| Error Code| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.          |
|33200004 | Invalid result.          |
|33200005 | Invalid size of eap data.          |
|33200009 | netmanager stop.          |
|33200099 | internal error.          |

```js
import {eap} from '@kit.NetworkKit';
let eapData:eap.EapData= {
  msgId: 1,
  eapBuffer: new Uint8Array([1, 2, 3, 4, 5]),
  bufferLen: 5,
};
let result = 1;

try {
  eap.replyCustomEapData(result, eapData);
  console.info('replyCustomEapData success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## eap.startEthEap

startEthEap(netId: number, profile: EthEapProfile): void

Starts EAP authentication on an Ethernet NIC.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                           | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| netId| number|Yes|ID of the Ethernet NIC. If the default value **-1** is specified, the system automatically matches the Ethernet NIC to initiate EAP authentication.|
| profile|[EthEapProfile](#etheapprofile) |Yes|EAP profile.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Extensible Authentication Error Codes](errorcode-net-eap.md).

| Error Code| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.          |
|33200001 | Invalid netId.          |
|33200003 | Invalid profile.          |
|33200009 | netmanager stop.          |
|33200010 | invalid eth state.          |
|33200099 | internal error.          |

**Example**

```js
import {eap} from '@kit.NetworkKit';
let netId = 100;
let profile: eap.EthEapProfile = {
  eapMethod: eap.EapMethod.EAP_TTLS,
  phase2Method: eap.Phase2Method.PHASE2_AKA_PRIME,
  identity: "identity",
  anonymousIdentity: "anonymousIdentity",
  password: "password",
  caCertAliases: "caCertAliases",
  caPath: "caPath",
  clientCertAliases: "clientCertAliases",
  certEntry: new Uint8Array([5,6,7,8,9,10]),
  certPassword: "certPassword",
  altSubjectMatch: "altSubjectMatch",
  domainSuffixMatch: "domainSuffixMatch",
  realm: "realm",
  plmn: "plmn",
  eapSubId: 1
};
    
try {
  eap.startEthEap(netId, profile);
  console.info('startEthEap success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## eap.logOffEthEap

logOffEthEap(netId: number): void

Revokes the EAP-authenticated state of an Ethernet NIC.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                           | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| netId | number|Yes|ID of the Ethernet NIC. If the default value **-1** is specified, the system automatically matches the Ethernet NIC to initiate EAP authentication.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Extensible Authentication Error Codes](errorcode-net-eap.md).

| Error Code| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.          |
|33200001 | Invalid netId.          |
|33200002 | Log off fail.          |
|33200009 | netmanager stop.          |
|33200010 | invalid eth state.          |
|33200099 | internal error.          |

**Example**

```js
import {eap} from '@kit.NetworkKit';
let netId = 100;    
try{
  eap.logOffEthEap(netId);
  console.info("logOffEthEap success");
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## eap.setEthEapConfig

setEthEapConfig(config: EthEapConfig): void

Sets the Ethernet 802.1X authentication configuration. The configuration is encrypted and persistently stored.

When this API is called multiple times, if any field in the config parameter changes, an automatic authentication process is triggered. If the 802.1X function or automatic authentication is disabled, the configuration is saved and automatic authentication is stopped. If the current authentication is initiated by an enterprise application through [eap.startEthEap](#eapstartetheap), only the configuration is saved and automatic authentication is not triggered, and the enterprise application retains the authentication control. The authentication result is returned through the callback registered by [eap.onStateChange](#eaponstatechange). A successful return of this API does not mean that the authentication succeeds.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [EthEapConfig](#etheapconfig) | Yes | Ethernet 802.1X authentication configuration to be set. When the sensitive fields password and certPassword in EthEapProfile are passed as empty strings, or certEntry is passed as an empty array, the original values are retained. When read through getEthEapConfig, password and certPassword return empty strings, and certEntry returns an empty array. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace the identity, password, certificate, and other configurations based on the actual authentication environment.
let profile: eap.EthEapProfile = {
  eapMethod: eap.EapMethod.EAP_PEAP,
  phase2Method: eap.Phase2Method.PHASE2_MSCHAPV2,
  identity: 'identity',
  anonymousIdentity: '',
  password: 'password',
  caCertAliases: 'caCertAliases',
  caPath: '',
  clientCertAliases: '',
  certEntry: new Uint8Array(0),
  certPassword: '',
  altSubjectMatch: '',
  domainSuffixMatch: 'example.com',
  realm: '',
  plmn: '',
  eapSubId: 0
};
let config: eap.EthEapConfig = {
  profile: profile,
  enabled: true,
  autoAuth: true,
  locked: false
};

try {
  eap.setEthEapConfig(config);
  console.info('setEthEapConfig success');
} catch (error) {
  let err = error as BusinessError;
  console.error(`setEthEapConfig failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.getEthEapConfig

getEthEapConfig(): Promise\<EthEapConfig\>

Obtains the saved Ethernet 802.1X authentication configuration. This API uses a promise to return the result asynchronously.

In the returned configuration, the sensitive fields **password** and **certPassword** in the profile are always empty strings, and **certEntry** is always an empty array.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<[EthEapConfig](#etheapconfig)\> | Promise object used to return the saved Ethernet 802.1X authentication configuration, in which **password** and **certPassword** are empty strings and **certEntry** is an empty array. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  eap.getEthEapConfig().then((config: eap.EthEapConfig) => {
    console.info(`enabled: ${config.enabled}, autoAuth: ${config.autoAuth}, locked: ${config.locked}`);
  }).catch((err: BusinessError) => {
    console.error(`getEthEapConfig failed. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`getEthEapConfig failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.deleteEthEapConfig

deleteEthEapConfig(): Promise\<void\>

Deletes the persisted Ethernet 802.1X EAP configuration. If an automatic authentication is in progress, this authentication process is stopped. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  eap.deleteEthEapConfig().then(() => {
    console.info('deleteEthEapConfig success');
  }).catch((err: BusinessError) => {
    console.error(`deleteEthEapConfig failed. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`deleteEthEapConfig failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.getEthEapStateInfo

getEthEapStateInfo(): EthEapStateInfo

Synchronously obtains the current Ethernet 802.1X authentication status information, including the authentication status, retry count, and supplementary information.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| [EthEapStateInfo](#etheapstateinfo) | Current Ethernet 802.1X authentication status information. |

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let stateInfo: eap.EthEapStateInfo = eap.getEthEapStateInfo();
  console.info(`state: ${stateInfo.state}, retryCount: ${stateInfo.retryCount}`);
} catch (error) {
  let err = error as BusinessError;
  console.error(`getEthEapStateInfo failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.onStateChange

onStateChange(callback: Callback\<EthEapStateInfo\>): void

Subscribes to the Ethernet 802.1X authentication status changes. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[EthEapStateInfo](#etheapstateinfo)\> | Yes | Callback invoked to return the Ethernet 802.1X authentication status information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callback = (stateInfo: eap.EthEapStateInfo): void => {
  console.info(`state: ${stateInfo.state}, retryCount: ${stateInfo.retryCount}`);
};

try {
  eap.onStateChange(callback);
  console.info('onStateChange success');
} catch (error) {
  let err = error as BusinessError;
  console.error(`onStateChange failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.offStateChange

offStateChange(callback?: Callback\<EthEapStateInfo\>): void

Unsubscribes from Ethernet 802.1X authentication status changes.

**Since:** 26.0.1

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[EthEapStateInfo](#etheapstateinfo)\> | No | Callback for the authentication status change event to unsubscribe from. It must be the same object as the callback passed in during subscription. If this parameter is not passed, all callbacks for this event are unsubscribed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callback = (stateInfo: eap.EthEapStateInfo): void => {
  console.info(`state: ${stateInfo.state}, retryCount: ${stateInfo.retryCount}`);
};

try {
  eap.onStateChange(callback);
  // When listening is no longer needed, pass the same callback function used during subscription.
  eap.offStateChange(callback);
  // When no callback function is passed, cancel all callbacks of this event.
  eap.offStateChange();
  console.info('offStateChange success');
} catch (error) {
  let err = error as BusinessError;
  console.error(`offStateChange failed. Code: ${err.code}, message: ${err.message}`);
}
```

## eap.connect

connect(action: EthEapConnectAction): Promise\<void\>

Manually triggers or disconnects Ethernet 802.1X authentication. This API uses a promise to return the result asynchronously.

When action is ACTION_CONNECT, the saved 802.1X authentication configuration is used to trigger authentication again. If no 802.1X authentication configuration is saved, the operation fails. The authentication result is returned through the callback registered by [eap.onStateChange](#eaponstatechange). If the current authentication is initiated by an enterprise application through eap.startEthEap, this API does not take effect and the original authentication is retained.

When action is ACTION_DISCONNECT, automatic authentication and retries are stopped, the current Ethernet 802.1X authentication is exited, and the authentication status is reset to [STATE_IDLE](#etheapstate).

**Since:** 26.0.1

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| action | [EthEapConnectAction](#etheapconnectaction) | Yes | Manual connection action. ACTION_CONNECT indicates triggering authentication again, and ACTION_DISCONNECT indicates disconnecting authentication. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Before calling, save the configuration through setEthEapConfig.
  // To disconnect authentication, replace action with eap.EthEapConnectAction.ACTION_DISCONNECT.
  eap.connect(eap.EthEapConnectAction.ACTION_CONNECT).then(() => {
    console.info('connect request completed');
  }).catch((err: BusinessError) => {
    console.error(`connect failed. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`connect failed. Code: ${err.code}, message: ${err.message}`);
}
```

## EapData

Defines the EAP data.

**System capability**: SystemCapability.Communication.NetManager.Eap

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| msgId | number | No| No| Pseudo random number used to associate the EAP data before and after processing.|
| eapBuffer | Uint8Array | No| No| Raw EAP data starting from the EAP header, which is not encrypted.|
| bufferLen| number | No | No | Data length. |

## CustomResult

Enumerates the EAP authentication results.

​**System capability**​: SystemCapability.Communication.NetManager.Eap

| **Name**| **Value**| **Description**|
| -------- | -------- | -------- |
| RESULT_FAIL | 0 | The authentication process ends with a failed result.|
| RESULT_NEXT | 1 | The authentication is successful, and the process proceeds to the next step.|
| RESULT_FINISH | 2 | The authentication process ends with a successful result.|

## EapMethod

Enumerates the EAP authentication methods.

**System capability**: SystemCapability.Communication.NetManager.Eap

| Name| Value| Description|
| -------- | -------- | -------- |
| EAP_NONE | 0 | Not specified.|
| EAP_PEAP | 1 | PEAP.|
| EAP_TLS | 2 | TLS.|
| EAP_TTLS | 3 | TTLS.|
| EAP_PWD | 4 | Password.|
| EAP_SIM | 5 | SIM.|
| EAP_AKA | 6 | AKA.|
| EAP_AKA_PRIME | 7 | AKA Prime.|
| EAP_UNAUTH_TLS | 8 | UNAUTH TLS.|

## Phase2Method

Enumerates the Phase 2 authentication methods.

**System capability**: SystemCapability.Communication.NetManager.Eap

| Name| Value| Description|
| -------- | -------- | -------- |
| PHASE2_NONE | 0 | Not specified.|
| PHASE2_PAP | 1 | PAP.|
| PHASE2_MSCHAP | 2 | MS-CHAP.|
| PHASE2_MSCHAPV2 | 3 | MS-CHAPv2.|
| PHASE2_GTC | 4 | GTC.|
| PHASE2_SIM | 5 | SIM.|
| PHASE2_AKA | 6 | AKA.|
| PHASE2_AKA_PRIME | 7 | AKA Prime.|

## EthEapProfile

Represents the EAP profile information.

**System capability**: SystemCapability.Communication.NetManager.Eap

| Name             | Type                         | Read-Only| Optional| Description                            |
| ----------------- | ----------------------------- | ---- |----| -------------------------------- |
| eapMethod         | [EapMethod](#eapmethod)      | No   | No | EAP authentication method.                     |
| phase2Method      | [Phase2Method](#phase2method)| No  | No| Phase 2 authentication method.              |
| identity          | string                        | No  | No| Identity information.                      |
| anonymousIdentity | string                        | No  | No| Anonymous identity.                      |
| password          | string                        | No  | No| Password.                          |
| caCertAliases     | string                        | No  | No| CA certificate alias.                   |
| caPath            | string                        | No  | No| CA certificate path.                   |
| clientCertAliases | string                        | No  | No| Client certificate alias.                |
| certEntry         | Uint8Array                    | No  | No| CA certificate content.                   |
| certPassword      | string                        | No  | No| CA certificate password.                    |
| altSubjectMatch   | string                        | No  | No| A string to match the alternate subject.                  |
| domainSuffixMatch | string                        | No  | No| A string to match the domain suffix.                    |
| realm             | string                        | No  | No| Realm for the passpoint credential.              |
| plmn              | string                        | No  | No| Public land mobile network (PLMN) of the passpoint credential provider.|
| eapSubId          | number                        | No  | No| Sub-ID of the SIM card.                   |

## EthEapConfig

Ethernet 802.1X authentication configuration, including EAP configuration information and the feature switch.

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| profile | [EthEapProfile](#etheapprofile) | No | No | EAP configuration information. When set through [eap.setEthEapConfig](#eapsetetheapconfig), passing an empty string for password and certPassword or an empty array for certEntry indicates retaining the original values. When obtained through [eap.getEthEapConfig](#eapgetetheapconfig), password and certPassword return empty strings, and certEntry returns an empty array. |
| enabled | boolean | No | No | Whether to enable the 802.1X feature. The value true indicates enabled, and false indicates disabled. |
| autoAuth | boolean | No | No | Whether to automatically initiate authentication when the network cable is connected or the device starts. The value true indicates automatic initiation, and false indicates no automatic initiation. |
| locked | boolean | No | No | Whether to lock the configuration. The value true indicates locked, and false indicates unlocked. After locking, the configuration cannot be modified except by unlocking. |

## EthEapState

Enumerates the Ethernet 802.1X authentication states.

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| STATE_IDLE | 0 | Idle state. Authentication has not been initiated. |
| STATE_AUTHENTICATING | 1 | Ethernet 802.1X authentication is in progress. |
| STATE_AUTHENTICATED | 2 | The authentication is successful. |
| STATE_FAILED | 3 | Authentication failed. The maximum number of retries has been reached. |
| STATE_RETRYING | 4 | Waiting for the next retry. |

## EthEapStateInfo

Represents the Ethernet 802.1X authentication status information. It can be obtained through [eap.getEthEapStateInfo](#eapgetetheapstateinfo) or returned by the callback registered through [eap.onStateChange](#eaponstatechange).

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| state | [EthEapState](#etheapstate) | No | No | Current authentication status. |
| retryCount | number | No | No | Current retry count, which is an integer and is reset to 0 after successful authentication. |
| message | string | No | Yes | Supplementary information, for example, the reason for authentication failure. It is empty when authentication succeeds. |

## EthEapConnectAction

Enumerates the Ethernet 802.1X authentication actions, used for [eap.connect](#eapconnect).

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| ACTION_CONNECT | 0 | Re-triggers authentication using the saved configuration. |
| ACTION_DISCONNECT | 1 | Stops automatic authentication and retries, exits the current Ethernet 802.1X authentication, and resets the authentication status to idle. |
