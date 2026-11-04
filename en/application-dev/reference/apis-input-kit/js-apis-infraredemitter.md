# @ohos.multimodalInput.infraredEmitter (IR Management)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c7eb0f7a0e5ece46961597d0139b9fc3f22f29e0 translatedAt=2026-11-04T04:35:54.165Z pushedAt=2026-11-04T08:04:44.683Z nl=1 -->

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

Generates an infrared signal with a specific frequency and level. Before calling this API, call [hasIrEmitter](#infraredemitterhasiremitter23) to check whether the device has an infrared emitter. If the device does not have an infrared emitter, calling this API takes no effect.

**Required permissions**: ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

**Parameters**

| Name      | Type                       | Mandatory  | Description                                      |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| infraredFrequency | number             | Yes   | IR frequency, in Hz.|
| pattern | Array&lt;number&gt; | Yes | Infrared level signal, in microseconds (μs). The number of level signals ranges from 0 to 1024. When the value is 0, the API call does not take effect. The value of each level signal must be greater than 0.<br/>For example, in the level signal array [100,200,300,400], 100 μs is a high level signal, 200 μs is a low level signal, 300 μs is a high level signal, and 400 μs is a low level signal. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
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
          // Query whether there is an infrared emitter.
          infraredEmitter.hasIrEmitter().then((result: boolean) => {
            if (result) {
              try {
                // Set the infrared frequency and infrared level signal mode.
                infraredEmitter.transmitInfrared(38000, [100, 200, 300, 400]);
              } catch (error) {
                console.error(`Failed to transmit infrared signal, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              }
            } else {
              console.info('The current device does not support IR emitter.');
            }
          }).catch((error: BusinessError) => {
            console.error(`Failed to query infrared emitter, Code: ${error.code}, message: ${error.message}.`);
          });
        })
    }
  }
}
```

## infraredEmitter.getInfraredFrequencies<sup>15+</sup>

getInfraredFrequencies(): Array&lt;InfraredFrequency&gt;

Queries the frequency range of infrared signals supported by the device. Before calling this API, call [hasIrEmitter](#infraredemitterhasiremitter23) to check whether the device has an infrared emitter.

**Required permissions**: ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**System capability**: SystemCapability.MultimodalInput.Input.InfraredEmitter

**Device behavior differences**: On Phone, Tablet, and TV devices that support an infrared emitter, this API returns the frequency range of infrared signals. On other devices that do not support an infrared emitter, this API returns a set of maximum and minimum frequencies, both of which are 0 Hz.

**Return value**

| Type                 | Description                 |
| ------------------- | ------------------- |
| Array&lt;[InfraredFrequency](#infraredfrequency15)&gt; | Frequency range of the infrared signal, including multiple groups of maximum and minimum frequencies.<br/>Since API version 23, when the device does not have an infrared emitter, a group of maximum and minimum frequencies is returned, both of which are 0 Hz. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message         |
| -------- | ----------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

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
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
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