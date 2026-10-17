# @ohos.net.eap (Extensible Authentication)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @foredward-->
<!--Designer: @h00918518-->
<!--Tester: @WIFIroam-test-->
<!--Adviser: @zhang_yixin13-->

The **eap** module provides the extensible authentication mechanism to enable third-party clients to access custom 802.1X (a port-based network access control protocol) authentication, such as Extensible Authentication Protocol (EAP) authentication. It also provides APIs for configuring Ethernet 802.1X EAP authentication, querying authentication state, and managing authentication state change callbacks.

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
| netType| number|Yes|Network type. The value can be **1** or **2**.<br>The value **1** indicates WLAN, and the value **2** indicates Ethernet.|
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
let  eapData = (eapData:eap.EapData):void => {
  console.info("rsp result",JSON.stringify(eapData))
}
    
try {
  eap.regCustomEapHandler(netType, eapCode, eapType, eapData);
  console.info('regCustomEapHandler success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## eap.unregCustomEapHandler

unregCustomEapHandler(netType:number, eapCode: number, eapType: number, callback: Callback\<EapData\>): void

Unregisters the custom handler of EAP packets for extensible authentication. This API returns the result asynchronously through a callback.

**Required permissions**: ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability**: SystemCapability.Communication.NetManager.Eap

**Parameters**

| Name                           | Type|Mandatory|Description|
| ----------------------------- | ---------- |---------- |---------- |
| netType| number|Yes|Network type. The value can be **1** or **2**.<br>The value **1** indicates WLAN, and the value **2** indicates Ethernet.|
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
let  eapData = (eapData:eap.EapData):void => {
  console.info("rsp result",JSON.stringify(eapData))
}
    
try {
  eap.unregCustomEapHandler(netType, eapCode, eapType, eapData);
  console.info('unregCustomEapHandler success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
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

Sets the 802.1X EAP configuration for Ethernet. The configuration is persisted in encrypted form. Any field change triggers one automatic authentication cycle unless 802.1X is disabled or authentication is currently occupied by an enterprise application. In the latter case, the configuration is persisted, while the enterprise application keeps control. The authentication result is delivered through the `onStateChange` callback, not by this API's return value.

For sensitive fields in `config.profile` (`password`, `certPassword`, and `certEntry`), an empty string or empty array preserves the corresponding value already stored. Do not log the configuration or its sensitive fields. When `locked` is `true`, configuration changes are denied; only an update that unlocks the configuration is allowed.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| config | [EthEapConfig](#etheapconfig) | Yes | Ethernet 802.1X EAP configuration. The `profile` property must include every required field defined by [EthEapProfile](#etheapprofile). |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

const config: eap.EthEapConfig = {
  profile: {
    eapMethod: eap.EapMethod.EAP_PEAP,
    phase2Method: eap.Phase2Method.PHASE2_MSCHAPV2,
    identity: 'identity-placeholder',
    anonymousIdentity: '',
    password: 'password-placeholder',
    caCertAliases: '',
    caPath: '',
    clientCertAliases: '',
    certEntry: new Uint8Array(),
    certPassword: '',
    altSubjectMatch: '',
    domainSuffixMatch: '',
    realm: '',
    plmn: '',
    eapSubId: 1
  },
  enabled: true,
  autoAuth: true,
  locked: false
};

try {
  eap.setEthEapConfig(config);
  console.info('setEthEapConfig succeeded');
} catch (err) {
  const error = err as BusinessError;
  console.error(`setEthEapConfig failed: ${error.code} - ${error.message}`);
}
```

## eap.getEthEapConfig

getEthEapConfig(): Promise\<EthEapConfig>

Gets the persisted Ethernet 802.1X EAP configuration. The configuration is persisted in encrypted form. Sensitive fields (`password`, `certPassword`, and `certEntry`) are always returned as empty values and cannot be read through this API. Do not log the returned configuration.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<[EthEapConfig](#etheapconfig)> | Promise used to return the persisted Ethernet 802.1X EAP configuration. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  eap.getEthEapConfig().then((config: eap.EthEapConfig) => {
    console.info(`getEthEapConfig succeeded. Enabled: ${config.enabled}`);
  }).catch((err: BusinessError) => {
    console.error(`getEthEapConfig failed: ${err.code} - ${err.message}`);
  });
} catch (err) {
  const error = err as BusinessError;
  console.error(`getEthEapConfig threw: ${error.code} - ${error.message}`);
}
```

## eap.deleteEthEapConfig

deleteEthEapConfig(): Promise\<void>

Deletes the persisted Ethernet 802.1X EAP configuration and stops any ongoing automatic authentication. This API is idempotent: it resolves successfully even when no configuration is stored.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  eap.deleteEthEapConfig().then(() => {
    console.info('deleteEthEapConfig succeeded');
  }).catch((err: BusinessError) => {
    console.error(`deleteEthEapConfig failed: ${err.code} - ${err.message}`);
  });
} catch (err) {
  const error = err as BusinessError;
  console.error(`deleteEthEapConfig threw: ${error.code} - ${error.message}`);
}
```

## eap.getEthEapStateInfo

getEthEapStateInfo(): EthEapStateInfo

Queries the current Ethernet 802.1X EAP authentication state information. The result includes the current state, retry count, and an optional supplementary message such as a failure reason. The message is empty on success.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| -------- | -------- |
| [EthEapStateInfo](#etheapstateinfo) | Current authentication state information. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const stateInfo: eap.EthEapStateInfo = eap.getEthEapStateInfo();
  console.info(`getEthEapStateInfo succeeded. State: ${stateInfo.state}`);
} catch (err) {
  const error = err as BusinessError;
  console.error(`getEthEapStateInfo failed: ${error.code} - ${error.message}`);
}
```

## eap.onStateChange

onStateChange(callback: Callback\<EthEapStateInfo>): void

Subscribes to Ethernet 802.1X EAP authentication state changes. Authentication results, including failures and successful authentication, are delivered through the callback.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[EthEapStateInfo](#etheapstateinfo)> | Yes | Callback used to return the current authentication state information. Keep the same callback reference when calling `offStateChange` to remove only this subscription. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (stateInfo: eap.EthEapStateInfo): void => {
  console.info(`Ethernet EAP state changed: ${stateInfo.state}`);
};

try {
  eap.onStateChange(callback);
  console.info('onStateChange succeeded');
} catch (err) {
  const error = err as BusinessError;
  console.error(`onStateChange failed: ${error.code} - ${error.message}`);
}
```

## eap.offStateChange

offStateChange(callback?: Callback\<EthEapStateInfo>): void

Unsubscribes from Ethernet 802.1X EAP authentication state changes. Pass the same callback reference used with `onStateChange` to remove that subscription, or omit `callback` to remove all state change subscriptions.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | Callback\<[EthEapStateInfo](#etheapstateinfo)> | No | Callback to remove. If omitted, all state change subscriptions are removed. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

const callback = (stateInfo: eap.EthEapStateInfo): void => {
  console.info(`Ethernet EAP state changed: ${stateInfo.state}`);
};

try {
  eap.onStateChange(callback);
  // Unregister using the same callback reference.
  eap.offStateChange(callback);
  // To remove all state change subscriptions, call eap.offStateChange().
  console.info('offStateChange succeeded');
} catch (err) {
  const error = err as BusinessError;
  console.error(`offStateChange failed: ${error.code} - ${error.message}`);
}
```

## eap.connect

connect(action: EthEapConnectAction): Promise\<void>

Manually triggers or disconnects Ethernet 802.1X EAP authentication. With `ACTION_CONNECT`, authentication is re-triggered with the saved configuration; the call fails if no configuration has been stored. With `ACTION_DISCONNECT`, automatic authentication is stopped and the underlying 802.1X authentication is logged off. If authentication is occupied by an enterprise application, this API does not interrupt that application; the result is delivered through the `onStateChange` callback.

**Since**: 26.2.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_EAP

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| action | [EthEapConnectAction](#etheapconnectaction) | Yes | Manual action: `ACTION_CONNECT` re-triggers authentication, or `ACTION_DISCONNECT` stops automatic authentication and logs off. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

| Error Code | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { eap } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  eap.connect(eap.EthEapConnectAction.ACTION_CONNECT).then(() => {
    console.info('connect succeeded');
  }).catch((err: BusinessError) => {
    console.error(`connect failed: ${err.code} - ${err.message}`);
  });
} catch (err) {
  const error = err as BusinessError;
  console.error(`connect threw: ${error.code} - ${error.message}`);
}
```

## EapData

Defines the EAP data.

​**System capability**: SystemCapability.Communication.NetManager.Eap

| **Name**| **Type**| **Read-Only**| **Optional**| **Description**|
| -------- | -------- | -------- | -------- | -------- |
| msgId | number | No| No| Pseudo random number used to associate the EAP data before and after processing.|
| eapBuffer | Uint8Array | No| No| Raw EAP data starting from the EAP header, which is not encrypted.|
| bufferLen| number | No| No| Data length.|

## CustomResult

Enumerates the EAP authentication results.

​**System capability**: SystemCapability.Communication.NetManager.Eap

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
| eapMethod         | [EapMethod](#eapmethod)      | No  | No| EAP authentication method.                    |
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

Represents the Ethernet 802.1X EAP configuration, including the EAP profile and feature switches. The configuration is persisted in encrypted form by [setEthEapConfig](#eapsetetheapconfig).

**Since**: 26.2.0

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| profile | [EthEapProfile](#etheapprofile) | No | No | EAP profile information. All fields defined by `EthEapProfile` are required. When setting the configuration, an empty string for `password` or `certPassword`, or an empty array for `certEntry`, preserves the stored value of that field. These three sensitive fields are always returned empty when reading the configuration. |
| enabled | boolean | No | No | Whether Ethernet 802.1X is enabled. `true`: enabled; `false`: disabled. |
| autoAuth | boolean | No | No | Whether to initiate authentication automatically when the network cable is connected or the device boots. `true`: automatically initiate authentication; `false`: do not automatically initiate authentication on these events. |
| locked | boolean | No | No | Whether the configuration is locked. `true`: locked; `false`: unlocked. When locked, configuration modifications are denied except for unlocking. |

## EthEapState

Enumerates the Ethernet 802.1X EAP authentication states.

**Since**: 26.2.0

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| STATE_IDLE | 0 | Idle. Authentication has not been initiated. |
| STATE_AUTHENTICATING | 1 | Authenticating. 802.1X authentication is in progress. |
| STATE_AUTHENTICATED | 2 | Authenticated. Authentication succeeded. |
| STATE_FAILED | 3 | Failed. The maximum retry count has been reached. |
| STATE_RETRYING | 4 | Retrying. Waiting before the next retry attempt. |

## EthEapStateInfo

Represents Ethernet 802.1X EAP authentication state information returned by [getEthEapStateInfo](#eapgetetheapstateinfo) or delivered through the [onStateChange](#eaponstatechange) callback.

**Since**: 26.2.0

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| state | [EthEapState](#etheapstate) | No | No | Current authentication state. |
| retryCount | number | No | No | Current retry count, which must be an integer and resets to 0 on success. |
| message | string | No | Yes | Supplementary message, such as the failure reason. Empty on success. |

## EthEapConnectAction

Enumerates the manual actions for Ethernet 802.1X EAP authentication.

**Since**: 26.2.0

**System capability**: SystemCapability.Communication.NetManager.Eap

**Model restriction**: This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| ACTION_CONNECT | 0 | Re-triggers authentication with the saved configuration. |
| ACTION_DISCONNECT | 1 | Stops automatic authentication and logs off the underlying 802.1X authentication. |
