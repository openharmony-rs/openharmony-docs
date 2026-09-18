# HceService

Provides APIs for implementing HCE, including receiving Application Protocol Data Units (APDUs) from the peer card reader and sending a response. Before using HCE-related APIs, check whether the device supports HCE.

**Since:** 8

**System capability:** SystemCapability.Communication.NFC.CardEmulation

## Modules to Import

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## off('hceCmd')

```TypeScript
off(type: 'hceCmd', callback?: AsyncCallback<number[]>): void
```

Unsubscribes from events indicating receiving of APDUs from the peer card reader. This API uses an asynchronous callback to return the result.

**Since:** 18

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hceCmd' | Yes | Event type. It has a fixed value of **hceCmd**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | No | Event callback. Each number is represented in hexadecimal notation, with values ranging from 0x00 to 0xFF. If this parameter is not set, this API unregisters the callback for the specified **type**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
// Applicable to devices other than lite wearables
import { hilog } from '@kit.PerformanceAnalysisKit';
import { cardEmulation } from '@kit.ConnectivityKit';
import { AsyncCallback } from '@kit.BasicServicesKit';
import { bundleManager, AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();
let element: bundleManager.ElementName;
const apduCallback: AsyncCallback<number[]> = (err, data) => {
  // Implement data processing and handle exceptions.
  console.info("AsyncCallback got apdu data");
};

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onCreate');
    element = {
      bundleName: want.bundleName ?? '',
      abilityName: want.abilityName ?? '',
      moduleName: want.moduleName
    };
    hceService.on('hceCmd', apduCallback);
  }
  onDestroy() {
    hilog.info(0x0000, 'testHce', '%{public}s', 'Ability onDestroy');
    hceService.off('hceCmd', apduCallback);
    hceService.stop(element);
  }
  // Other functions in the lifecycle
}
```

## on('hceCmd')

```TypeScript
on(type: 'hceCmd', callback: AsyncCallback<number[]>): void
```

Subscribes to events indicating receiving of APDUs from the peer card reader. The application needs to call this API in **onCreate()** of the HCE page. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'hceCmd' | Yes | Event type. It has a fixed value of **hceCmd**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | Yes | Event callback used to return the data array that complies with the APDU. Each number is represented in hexadecimal notation, with values ranging from 0x00 to 0xFF. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter.<br>**Applicable version:** 12 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
ArkTS example:
```

```TypeScript
JS example:
```

## sendResponse

```TypeScript
sendResponse(responseApdu: number[]): void
```

Sends a response to the peer card reader.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [transmit](#transmit) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [transmit](#transmit)

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| responseApdu | number[] | Yes | Response APDU sent to the peer card reader. The value consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Examples**

```TypeScript
ArkTS example:

For details, see the example of [transmit](#transmit).

JS example:
```

```TypeScript
/* Applicable to lite wearables */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// Applicable to lite wearables
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.on("hceCmd", (err, res) => {
            if(err.data === 0) {
                console.info('callback => Operation hceCmd succeeded. Data: ${JSON.stringify(res)}');
                hceService.sendResponse([0x00,0xa4,0x04,0x00,
                    0x0e,0x32,0x50,0x41,0x59,0x2e,0x53,0x59,0x53,0x2e,0x44,0x44,
                    0x46,0x30,0x31,0x00]);
            } else {
                console.info('callback => Operation hceCmd failed. Cause: ${JSON.stringify(err.data)}');
            }
        });
    }
}
```

## start

```TypeScript
start(elementName: ElementName, aidList: string[]): void
```

Starts HCE, including enabling this application to run in the foreground preferentially and dynamically registering the AID list.

**Since:** 9

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the page, on which the application declares the NFC card emulation capability. It must contain at least **bundleName** and **abilityName** and cannot be empty. |
| aidList | string[] | Yes | List of AIDs to register. This parameter can be left empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-abnormal-nfc-card-emulation-status) | Card emulation running state is abnormal in service. |

## startHCE

```TypeScript
startHCE(aidList: string[]): boolean
```

Starts HCE, including enabling this application to run in the foreground preferentially and dynamically registering the AID list.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [start](#start) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [start](#start)

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aidList | string[] | Yes | List of AIDs to register. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if HCE is started or has been started; returns **false** otherwise. |

**Examples**

```TypeScript
ArkTS example:

For details, see the example of on.

JS example:
```

```TypeScript
/* Applicable to lite wearables */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// Applicable to lite wearables
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.startHCE([
            "F0010203040506", "A0000000041010"
        ]);
    }
}
```

## stop

```TypeScript
stop(elementName: ElementName): void
```

Stops HCE, including canceling the subscription of APDU data, exiting this application from the foreground, and releasing the dynamically registered AID list. The application needs to call this API in **onDestroy** of the HCE page.

**Since:** 9

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | Yes | Information about the page, on which the application declares the NFC card emulation capability. It must contain at least **bundleName** and **abilityName** and cannot be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-abnormal-nfc-card-emulation-status) | Card emulation running state is abnormal in service. |

## stopHCE

```TypeScript
stopHCE(): boolean
```

Stops HCE, including exiting the current application from the foreground, releasing the dynamically registered AID list, and canceling the subscription of **hceCmd**.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [stop](#stop) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stop](#stop)

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if HCE is stopped or disabled; **false** otherwise. |

**Examples**

```TypeScript
ArkTS example:

For details, see the example of on.

JS example:
```

```TypeScript
/* Applicable to lite wearables */
/* xxx.css */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}
.button {
  font-size: 30px;
  text-align: center;
  width: 200px;
  height: 100px;
}
```

```TypeScript
// Applicable to lite wearables
// xxx.js
import cardEmulation from '@ohos.nfc.cardEmulation';

export default  {
    data: {
        fontSize: '30px',
        fontColor: '#FF1AFF00',
    },
    onClick() {
        var hceService = new cardEmulation.HceService();
        hceService.stopHCE();
    }
}
```

## transmit

```TypeScript
transmit(response: number[]): Promise<void>
```

Transmits an APDU to the peer card reader. This API uses a promise to return the result. The application calls this API only after receiving an APDU sent by the card reader via on.

**Since:** 9

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | number[] | Yes | Response APDU sent to the peer card reader. The value consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-abnormal-nfc-card-emulation-status) | Card emulation running state is abnormal in service. |

**Examples**

```TypeScript
// Applicable to devices other than lite wearables
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();

// Data to be sent by the application. The following data is for reference only.
const responseData = [0x1, 0x2];
hceService.transmit(responseData).then(() => {
  // Process the promise.
  console.info("transmit Promise success.");
}).catch((err: BusinessError) => {
  console.error("transmit Promise error:", err);
});
```

```TypeScript
// Applicable to lite wearables
import cardEmulation from '@ohos.nfc.cardEmulation';

let hceService = new cardEmulation.HceService();

// Data to be sent by the application. The following data is for reference only.
let responseData = [0x1, 0x2];
hceService.transmit(responseData).then(() => {
  // Process the promise.
  console.info("transmit Promise success.");
});
console.info("transmit Promise end.");
```

```TypeScript
// Applicable to devices other than lite wearables
import { cardEmulation } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hceService: cardEmulation.HceService = new cardEmulation.HceService();

// Data to be sent by the application. The following data is for reference only.
try {
  const responseData = [0x1, 0x2];

  hceService.transmit(responseData, (err : BusinessError)=> {
    if (err) {
      console.error(`transmit AsyncCallback err Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info("transmit AsyncCallback success.");
    }
  });
} catch (error) {
  console.error(`transmit AsyncCallback catch Code: ${(error as BusinessError).code}, ` +
    `message: ${(error as BusinessError).message}`);
}
```

```TypeScript
// Applicable to lite wearables
import cardEmulation from '@ohos.nfc.cardEmulation';

let hceService = new cardEmulation.HceService();

// Data to be sent by the application. The following data is for reference only.
let responseData = [0x1, 0x2];
hceService.transmit(responseData, () => {
  console.info("transmit Promise success.");
});
console.info("transmit Promise end.");
```

## transmit

```TypeScript
transmit(response: number[], callback: AsyncCallback<void>): void
```

Sends APDU data to the peer card reader. The application can call this API only after receiving an APDU sent by the card reader via on. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NFC_CARD_EMULATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.CardEmulation

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | number[] | Yes | Response APDU sent to the peer card reader. The value consists of hexadecimal numbers ranging from **0x00** to **0xFF**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100301](../errorcode-nfc.md#3100301-abnormal-nfc-card-emulation-status) | Card emulation running state is abnormal in service. |

**Examples**

See [transmit](#transmit)
