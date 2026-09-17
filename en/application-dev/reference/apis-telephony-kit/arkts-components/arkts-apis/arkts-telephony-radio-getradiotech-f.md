# getRadioTech

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getRadioTech

```TypeScript
function getRadioTech(slotId: number, callback: AsyncCallback<NetworkRadioTech>): void
```

Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. This API uses an asynchronous callback to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 6

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md)&gt; | Yes | Callback used to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getRadioTech(slotId, (err: BusinessError, data: radio.NetworkRadioTech) => {
    if (err) {
        console.error(`getRadioTech failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getRadioTech success, callback: data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getRadioTech(slotId).then((data: radio.NetworkRadioTech) => {
    console.info(`getRadioTech success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getRadioTech failed, promise: err->${JSON.stringify(err)}`);
});
```


## getRadioTech

```TypeScript
function getRadioTech(slotId: number): Promise<NetworkRadioTech>
```

Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. This API uses a promise to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 6

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{psRadioTech: RadioTechnology, csRadioTech: RadioTechnology}&gt; | Promise used to return the result. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.<br>**Since:** 6 - 10 |
| Promise&lt;[NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md)&gt; | Returns the RAT of PS domain and CS domain of registered network. The values of RAT are as follows: &lt;ul&gt; &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_UNKNOWN` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_GSM` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_1XRTT` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_WCDMA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_HSPA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_HSPAP` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_TD_SCDMA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_EVDO` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_EHRPD` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_LTE` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_LTE_CA` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_IWLAN` &lt;li&gt;`RadioTechnology#RADIO_TECHNOLOGY_NR` &lt;/ul&gt;<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

See [getRadioTech](#getradiotech)
