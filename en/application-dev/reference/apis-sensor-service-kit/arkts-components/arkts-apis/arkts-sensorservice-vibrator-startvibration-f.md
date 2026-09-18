# startVibration

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## startVibration

```TypeScript
function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback<void>): void
```

Starts vibration based on a specified effect and attribute. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.VIBRATE

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | Yes | Vibration effect. The following options are supported:<br>1. [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md): triggers vibration according to preset vibration effects. This mode is suitable for short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, dragging, etc.). This API is recommended to maintain consistency with the system's overall vibration feedback experience.<br>2. [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md): triggers vibration according to custom vibration configuration file. This mode is suitable for interactive feedback in complex scenarios requiring precise vibration patterns (such as realistic effects triggered by emoji packs, or feedback for in-game actions /mechanics).<br>3. [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md): triggers vibration of the specified duration, providing basic control over the start and stop of vibration. This mode does not support customization of vibration intensity, frequency, or other parameters. As a result, the vibration adjustment is relatively coarse and not suitable for delivering a refined experience.<br>4. [VibrateFromPattern&lt;sup&gt;18+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibratefrompattern-i.md): starts vibration according to a custom vibration pattern. The usage scenario is the same as **VibrateFromFile**. **VibrateFromFile** utilizes predefined effects in a custom configuration file, passing specific vibration events to the API via file descriptors. By contrast, **VibrateFromPattern** enables more flexible vibration event combinations, delivering them to the API as a vibration event array.<br> |
| attribute | [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | Yes | Vibration attribute. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the operation result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object, which contains the error code and error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed |

**Examples**

```TypeScript
Trigger vibration based on a preset effect.
```

```TypeScript
Trigger vibration based on a custom vibration configuration file.
```

```TypeScript
Trigger vibration based on a specified duration.
```


## startVibration

```TypeScript
function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise<void>
```

Starts vibration based on a specified effect and attribute. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.VIBRATE

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | Yes | Vibration effect. The following options are supported:<br>1. [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md): triggers vibration according to preset vibration effects. This mode is suitable for short vibration scenarios in interactive feedback (such as tapping, long-pressing, sliding, dragging, etc.). This API is recommended to maintain consistency with the system's overall vibration feedback experience.<br>2. [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md): triggers vibration according to custom vibration configuration file. This mode is suitable for interactive feedback in complex scenarios requiring precise vibration patterns (such as realistic effects triggered by emoji packs, or feedback for in-game actions /mechanics).<br>3. [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md): triggers vibration of the specified duration, providing basic control over the start and stop of vibration. This mode does not support customization of vibration intensity, frequency, or other parameters. As a result, the vibration adjustment is relatively coarse and not suitable for delivering a refined experience.<br>4. [VibrateFromPattern&lt;sup&gt;18+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibratefrompattern-i.md): starts vibration according to a custom vibration pattern. The usage scenario is the same as **VibrateFromFile**. **VibrateFromFile** utilizes predefined effects in a custom configuration file, passing specific vibration events to the API via file descriptors. By contrast, **VibrateFromPattern** enables more flexible vibration event combinations, delivering them to the API as a vibration event array. |
| attribute | [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | Yes | Vibration attribute. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [14600101](../errorcode-vibrator.md#14600101-device-operation-failed) | Device operation failed. |

**Examples**

See [startVibration](#startvibration)
