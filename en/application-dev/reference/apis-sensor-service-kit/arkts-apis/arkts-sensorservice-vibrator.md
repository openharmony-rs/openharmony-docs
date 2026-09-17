# @ohos.vibrator

The **vibrator** module allows precise control over the vibration of device vibrators. With the APIs provided by this module, you can start vibration in various modes such as specified duration, preset effect, and custom effect and stop any or all of them.

**Since:** 8

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getEffectInfoSync](arkts-sensorservice-vibrator-geteffectinfosync-f.md) | Obtains the preset vibration effect based on the device ID and vibrator ID to determine whether the preset vibration effect is supported. |
| [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md) | Queries the vibrator list of one or all devices. |
| [isHdHapticSupported](arkts-sensorservice-vibrator-ishdhapticsupported-f.md) | Checks whether HD vibration is supported. |
| [isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md) | Checks whether an effect ID is supported. This API uses an asynchronous callback to return the result. |
| [isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md) | Checks whether an effect ID is supported. This API uses a promise to return the result. |
| [isSupportEffectSync](arkts-sensorservice-vibrator-issupporteffectsync-f.md) | Checks whether the preset vibration effect is supported. |
| [off](arkts-sensorservice-vibrator-off-f.md#offvibratorstatechange) | Disables listening for vibrator status changes. |
| [on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange) | Enables listening for vibrator status changes. |
| [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) | Starts vibration based on a specified effect and attribute. This API uses an asynchronous callback to return the result. |
| [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) | Starts vibration based on a specified effect and attribute. This API uses a promise to return the result. |
| [stop](arkts-sensorservice-vibrator-stop-f.md) | Stops vibration in the specified mode. This API uses a promise to return the result. |
| [stop](arkts-sensorservice-vibrator-stop-f.md) | Stops vibration in the specified mode. This API uses an asynchronous callback to return the result. |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md) | Stops vibration in the specified mode. This API uses a promise to return the result. |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md) | Stops vibration in the specified mode. This API uses an asynchronous callback to return the result. |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md) | Stops vibration in all modes. This API uses an asynchronous callback to return the result. |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md) | Stops vibration in all modes. This API uses a promise to return the result. |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md) | Stops vibration based on the specified vibrator parameters. If no parameters are passed, this API stops all vibrators of the local device by default. This API uses a promise to return the result. |
| [stopVibrationSync](arkts-sensorservice-vibrator-stopvibrationsync-f.md) | Stops any form of motor vibration. |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md) | Triggers vibration based on a specified duration. This API uses an asynchronous callback to return the result. |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md) | Triggers vibration based on a specified duration. This API uses a promise to return the result. |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md) | Triggers vibration based on a specified effect. This API uses a promise to return the result. |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md) | Triggers vibration based on a specified effect. This API uses an asynchronous callback to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [VibratorPatternBuilder](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md) | Provide methods for adding long or short vibration events and generate VibratorPattern objects. |

### Interfaces

| Name | Description |
| --- | --- |
| [ContinuousParam](arkts-sensorservice-vibrator-continuousparam-i.md) | Defines the parameters for continuous vibration. |
| [EffectInfo](arkts-sensorservice-vibrator-effectinfo-i.md) | Defines the preset effect. |
| [HapticFileDescriptor](arkts-sensorservice-vibrator-hapticfiledescriptor-i.md) | Describes the FD of a custom vibration configuration file. Ensure that the file is available, and the parameters in it can be obtained from the sandbox path through the [fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen) API or from the HAP resource through the [getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd) API. The application scenario is as follows: The vibration sequence is stored in a file and vibration needs to be triggered based on the offset and length. For details about the storage format of the vibration sequence, see [Vibration Effect Description](../../../device/sensor/vibrator-guidelines.md#vibration-effect-description). |
| [TransientParam](arkts-sensorservice-vibrator-transientparam-i.md) | Defines the parameters for transient vibration. |
| [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | Describes the vibration attribute. |
| [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md) | Represents a custom vibration pattern. It is supported only by certain devices. An error code will be returned if a device does not support this vibration mode. You can pass **VibrateFromFile** to [VibrateEffect9+](arkts-sensorservice-vibrator-vibrateeffect-t.md) to specify a custom vibration pattern when calling [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md). |
| [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md) | Defines the custom vibration effect. |
| [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) | Represents the preset vibration effect. You can pass **VibratePreset** to [VibrateEffect9+](arkts-sensorservice-vibrator-vibrateeffect-t.md) to specify a preset vibration effect when calling [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md). |
| [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md) | Represents vibration of the specified duration. |
| [VibratorCurvePoint](arkts-sensorservice-vibrator-vibratorcurvepoint-i.md) | Defines the gain relative to the vibration intensity. |
| [VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md) | Vibration event. |
| [VibratorInfo](arkts-sensorservice-vibrator-vibratorinfo-i.md) | Defines the vibrator information. |
| [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | Defines the vibrator parameters. If **VibratorInfoParam** is left unspecified, an API applies to all vibrators of the local device by default. |
| [VibratorPattern](arkts-sensorservice-vibrator-vibratorpattern-i.md) | Defines the vibration sequence. |
| [VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md) | Defines the vibrator status change event. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i-sys.md) | Describes the vibration attribute. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [EffectId](arkts-sensorservice-vibrator-effectid-e.md) | Enumerates the preset vibration effect IDs. This parameter is needed when you call [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.stopVibration9+](arkts-sensorservice-vibrator-stopvibration-f.md) to deliver the vibration effect specified by [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md). This parameter supports a variety of values, such as **haptic.clock.timer**. [HapticFeedback&lt;sup&gt;12+&lt;/sup&gt;](arkts-sensorservice-vibrator-hapticfeedback-e.md) provides several frequently used **EffectId** values. |
| [HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md) | Defines the vibration effect. The frequency of the same vibration effect may vary depending on the vibrator, but the frequency trend remains consistent. These vibration effects correspond to the specific **EffectId** values. For details, see the sample code that demonstrates how to use [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.stopVibration9+](arkts-sensorservice-vibrator-stopvibration-f.md) to deliver the vibration effect defined by [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md). |
| [VibratorEventType](arkts-sensorservice-vibrator-vibratoreventtype-e.md) | Vibration event type. |
| [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | Enumerates vibration stop modes. This parameter is required for [vibrator.stopVibration9+](arkts-sensorservice-vibrator-stopvibration-f.md) or [vibrator.stopVibration9+](arkts-sensorservice-vibrator-stopvibration-f.md). The stop mode must match that delivered in [VibrateEffect9+](arkts-sensorservice-vibrator-vibrateeffect-t.md). |

### Types

| Name | Description |
| --- | --- |
| [Usage](arkts-sensorservice-vibrator-usage-t.md) | Enumerates the vibration scenarios. |
| [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | Enumerates vibration effects of the vibrator. You can specify the vibration effect when calling [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md). |
