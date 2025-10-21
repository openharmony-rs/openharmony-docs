# @ohos.connectedTag (Active Tags)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @bitbegin-->
<!--Designer: @guofan912-->
<!--Tester: @wuqingyang1-->
<!--Adviser: @zhang_yixin13-->

The **connectedTag** module provides APIs for using active tags. You can use the APIs to initialize the active tag chip and read and write active tags.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { connectedTag } from '@kit.ConnectivityKit';
```

## connectedTag.init<sup>(deprecated)</sup>

init(): boolean

Initializes the active tag chip.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [initialize](#connectedtaginitialize9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| boolean | **true**: The initialization is successful.&nbsp;<br>**false**: The initialization fails.|

## connectedTag.initialize<sup>9+</sup>

initialize(): void

Initializes the active tag chip.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

## connectedTag.uninit<sup>(deprecated)</sup>

uninit(): boolean

Uninitializes the active tag resources.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [uninitialize](#connectedtaguninitialize9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| boolean | **true**: The uninstallation is successful.&nbsp;<br>**false**: The uninstallation fails.|

## connectedTag.uninitialize<sup>9+</sup>

uninitialize(): void

Uninitializes the active tag resources.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

## connectedTag.readNdefTag<sup>(deprecated)</sup>

readNdefTag(): Promise&lt;string&gt;

Reads the content of this active tag. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [uninitialize](#connectedtaguninitialize9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the content of the active tag.|

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

connectedTag.readNdefTag().then((data) => {
    console.info("connectedTag readNdefTag Promise data = " + data);
}).catch((err: BusinessError)=> {
    console.error("connectedTag readNdefTag Promise err: " + err);
});
```

## connectedTag.read<sup>9+</sup>

read(): Promise&lt;number[]&gt;

Reads the content of this active tag. This API uses a promise to return the result.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;number[]&gt; | Promise used to return the content of the active tag.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

connectedTag.read().then((data) => {
    console.info("connectedTag read Promise data = " + data);
}).catch((err: BusinessError)=> {
    console.error("connectedTag read Promise err: " + err);
});
```

## connectedTag.readNdefTag<sup>(deprecated)</sup>

readNdefTag(callback: AsyncCallback&lt;string&gt;): void

Reads the content of this active tag. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [uninitialize](#connectedtaguninitialize9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;string&gt; | Yes| Callback used to return the active tag content obtained.|

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';

connectedTag.readNdefTag((err, data)=> {
    if (err) {
        console.error("connectedTag readNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag readNdefTag AsyncCallback data: " + data);
    }
});
```

## connectedTag.read<sup>9+</sup>

read(callback: AsyncCallback&lt;number[]&gt;): void

Reads the content of this active tag. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;number[]&gt; | Yes| Callback used to return the active tag content obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';

connectedTag.read((err, data)=> {
    if (err) {
        console.error("connectedTag read AsyncCallback err: " + err);
    } else {
        console.info("connectedTag read AsyncCallback data: " + data);
    }
});
```

## connectedTag.writeNdefTag<sup>(deprecated)</sup>

writeNdefTag(data: string): Promise&lt;void&gt;

Writes data to this active tag. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [connectedTag.write](#connectedtagwrite9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| data | string | Yes| Data to be written to the active tag. The maximum length is 1024 bytes.|

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData).then(() => {
    console.info("connectedTag.writeNdefTag Promise success.");
}).catch((err: BusinessError)=> {
    console.error("connectedTag.writeNdefTag Promise err: " + err);
});
```

## connectedTag.write<sup>9+</sup>

write(data: number[]): Promise&lt;void&gt;

Writes data to this active tag. This API uses a promise to return the result.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| data | number[] | Yes| Data to be written to the active tag. The value is a hexadecimal number ranging from 0x00 to 0xFF.|

**Return value**

| **Type**| **Description**|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|401 | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rawData = [0x01, 0x02, 0x03]; // change it to be correct.
connectedTag.write(rawData).then(() => {
    console.info("connectedTag.writeNdefTag Promise success.");
}).catch((err: BusinessError)=> {
    console.error("connectedTag.writeNdefTag Promise err: " + err);
});
```

## connectedTag.writeNdefTag<sup>(deprecated)</sup>

writeNdefTag(data: string, callback: AsyncCallback&lt;void&gt;): void

Writes data to this active tag. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [connectedTag.write](#connectedtagwrite9) instead.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| data | string | Yes| Data to be written to the active tag. The maximum length is 1024 bytes.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the active tag content obtained.|

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData, (err)=> {
    if (err) {
        console.error("connectedTag.writeNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag.writeNdefTag AsyncCallback success.");
    }
});
```

## connectedTag.write<sup>9+</sup>

write(data: number[], callback: AsyncCallback&lt;void&gt;): void

Writes data to this active tag. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| data | number[] | Yes| Data to be written to the active tag. The value is a hexadecimal number ranging from 0x00 to 0xFF.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the active tag content obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [NFC Error Codes](errorcode-nfc.md).

| ID| Error Message|
| -------- | -------- |
|201 | Permission denied.                 |
|401 | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
|801 | Capability not supported.          |
|3200101 | Connected NFC tag running state is abnormal in service. |

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';

let rawData = [0x01, 0x02, 0x03]; // change it to be correct.
connectedTag.write(rawData, (err)=> {
    if (err) {
        console.error("connectedTag.writeNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag.writeNdefTag AsyncCallback success.");
    }
});
```

## connectedTag.on('notify')

on(type: "notify", callback: Callback&lt;number&gt;): void

Registers the NFC field strength state events.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. This parameter has a fixed value of **notify**.|
| callback | Callback&lt;number&gt; | Yes| Callback used to return the [NfcRfType](#nfcrftype).|

## connectedTag.off('notify')

off(type: "notify", callback?: Callback&lt;number&gt;): void

Unregisters the NFC field strength state events.

**Required permissions**: ohos.permission.NFC_TAG

**System capability**: SystemCapability.Communication.ConnectedTag

**Parameters**

| **Name**| **Type**| **Mandatory**| **Description**|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. This parameter has a fixed value of **notify**.|
| callback | Callback&lt;number&gt; | No| Callback used to return the field strength state. If this parameter is not specified, all callbacks associated with the specified event will be unregistered.|

**Example**

```js
import { connectedTag } from '@kit.ConnectivityKit';

function nfcStatusCb(rfState: connectedTag.NfcRfType) {
    console.info("connectedTag on Callback rfState: ", rfState);
}

// Process of using an active NFC tag
async function nfcTagTestOn(): Promise<void> {
    try {
        console.info("connectedTag initialize");
        connectedTag.initialize();
    } catch (error) {
        console.error("initialize error:" + error);
    }
    // Register a callback for NFC status change events.
    connectedTag.on("notify", nfcStatusCb);
    try {
        let tag = [3, 1, 0];
        console.info("connectedTag write: tag=" + tag);
        await connectedTag.write(tag);
        let data = await connectedTag.read();
        console.info("connectedTag read: data=" + data);
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}

// Unregister the callback for NFC status change events and uninitialize the NFC tag.
async function nfcTagTestOff(): Promise<void> {
    // Unregister the callback for NFC status change events.
    connectedTag.off("notify", nfcStatusCb);
    try {
        console.info("connectedTag uninitialize");
        connectedTag.uninitialize();
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}

export { nfcTagTestOn, nfcTagTestOff }
```

## NfcRfType

Enumerates the NFC field strength states.

**System capability**: SystemCapability.Communication.ConnectedTag

| Name| Value| Description|
| -------- | -------- | -------- |
| NFC_RF_LEAVE | 0 | NFC exit.|
| NFC_RF_ENTER | 1 | NFC entry.|
