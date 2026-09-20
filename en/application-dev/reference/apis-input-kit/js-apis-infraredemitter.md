# @ohos.multimodalInput.infraredEmitter (IR Management)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a42f8feedc5dcea22b2974f472d01ab7526f02c7 translatedAt=2026-09-01T01:19:35.451Z pushedAt=2026-09-03T06:40:38.965Z -->

The **infraredEmitter** module generates IR signals of the specified frequency and size, and queries the frequency range supported by the device.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>

## Modules to Import

```js
import { infraredEmitter } from '@kit.InputKit';
```

## infraredEmitter.transmitInfrared<sup>15+</sup>

transmitInfrared(infraredFrequency: number, pattern: Array&lt;number&gt;): void

Generates IR signals at the specified frequency and level.

**Required permissions**: ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

**Parameters**

| Name      | Type                       | Mandatory  | Description                                      |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| infraredFrequency | number             | Yes   | IR frequency, in Hz.|
| pattern | Array&lt;number&gt; | Yes    | Infrared level signal, in microseconds (μs). The number of infrared level signals ranges from 0 to 1024. The value of this parameter must be greater than 0. If this parameter is set to **0**, the API does not take effect. <br/>For example, in the level signal array [100,200,300,400], **100** indicates a high-level signal, **200** indicates a low-level signal, **300** is a high-level signal, and **400** is a low-level signal. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // Set the infrared frequency and infrared level signal mode.
            infraredEmitter.transmitInfrared(38000, [100, 200, 300, 400]);
          } catch (error) {
            console.error(`Failed to transmit infrared signal, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## infraredEmitter.getInfraredFrequencies<sup>15+</sup>

getInfraredFrequencies(): Array&lt;InfraredFrequency&gt;

Queries the frequency range of the infrared signals supported by the device. It is recommended that you first use [hasIrEmitter](#infraredemitterhasiremitter23) to check whether the device supports an infrared emitter.

**Required permissions**: ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

**Device behavior differences**: On phones and TVs that support IR emitters, this API returns the frequency range of IR signals. On devices that do not support IR emitters, this API returns one group of maximum and minimum frequencies, both of which are 0 Hz. You are advised to use the [hasIrEmitter](#infraredemitterhasiremitter23) API to check whether a device supports IR emitters.

**Return value**

| Type                 | Description                 |
| ------------------- | ------------------- |
| Array&lt;[InfraredFrequency](#infraredfrequency15)&gt; | Frequency range of the infrared signal, containing multiple sets of maximum and minimum frequencies.<br/>Since API version 23, when the device does not have an infrared emitter, a set of maximum and minimum frequencies is returned, both 0 Hz. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 201 | Permission denied. |

**Example**

```js
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let frequencies = infraredEmitter.getInfraredFrequencies();
            console.info(`Succeeded in getting infrared frequencies, frequencies: ${JSON.stringify(frequencies)}.`);
          } catch (error) {
            console.error(`Failed to get infrared frequencies, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## InfraredFrequency<sup>15+</sup>

Defines the frequency range of IR signals.

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

| Name       | Type  | Read-Only  | Optional  | Description     |
| --------- | ------ | ---- | ---- | ------- |
| max    | number  | No   | No| Maximum frequency, in Hz.|
| min    | number  | No   | No| Minimum frequency, in Hz.|

## infraredEmitter.hasIrEmitter<sup>23+</sup>

hasIrEmitter(): Promise&lt;boolean&gt;

Checks whether the device has an infrared transmitter. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

**Return value**

| Type                 | Description                 |
| ------------------- | ------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** is returned if the device has an infrared emitter, and **false** is returned if the device does not have an infrared emitter.|

**Error codes**

For details about the error codes, see [IR Management Error Codes](errorcode-infraredemitter.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 201 | Permission denied. |
| 3800001 | Input service exception. |

**Example**

```js
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
            // Query Whether There Is an Infrared Emitter
            infraredEmitter.hasIrEmitter().then((result: boolean) => {
              console.info(`Succeeded in querying infrared emitter: ${JSON.stringify(result)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to query infrared emitter, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`)})
        })
    }
  }
}
```