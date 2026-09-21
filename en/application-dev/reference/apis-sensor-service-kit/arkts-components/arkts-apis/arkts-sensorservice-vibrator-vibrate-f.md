# vibrate

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## vibrate

```TypeScript
function vibrate(duration: number, callback?: AsyncCallback<void>): void
```

Triggers vibration based on a specified duration. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | Vibration duration, in ms. The value range is (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10s to maximize user experience. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If the vibration starts, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(1000, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
```


<a id="vibrate-1"></a>

## vibrate

```TypeScript
function vibrate(duration: number): Promise<void>
```

Triggers vibration based on a specified duration. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1)(effect: VibrateEffect, attribute: VibrateAttribute)

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | Vibration duration, in ms. The value range is (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10s to maximize user experience. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns the result. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(1000).then(() => {
  console.info('Succeed in vibrating');
}, (error: BusinessError) => {
  console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
});
```


<a id="vibrate-2"></a>

## vibrate

```TypeScript
function vibrate(effectId: EffectId): Promise<void>
```

Triggers vibration based on a specified effect. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1)(effect: VibrateEffect, attribute: VibrateAttribute)

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effectId | [EffectId](arkts-sensorservice-vibrator-effectid-e.md) | Yes | Effect ID. The value is a string of a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. You are advised to check whether the effect ID is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns the result. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER).then(() => {
  console.info('Succeed in vibrating');
}, (error: BusinessError) => {
  console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
});
```


<a id="vibrate-3"></a>

## vibrate

```TypeScript
function vibrate(effectId: EffectId, callback?: AsyncCallback<void>): void
```

Triggers vibration based on a specified effect. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effectId | [EffectId](arkts-sensorservice-vibrator-effectid-e.md) | Yes | Effect ID. The value is a string of a maximum of 64 characters. If the length exceeds 64 characters, the first 64 characters are used. You are advised to check whether the effect ID is supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If the vibration starts, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
```
