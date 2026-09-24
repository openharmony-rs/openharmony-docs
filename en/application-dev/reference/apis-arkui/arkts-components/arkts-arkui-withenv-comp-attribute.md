# WithEnv properties/events

```TypeScript
export declare class WithEnvAttribute
```

Supports the following **WithEnv**-specific attributes.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are not supported.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { WithEnv, WithEnvAttribute} from '@kit.ArkUI';
```

## customEnv

```TypeScript
customEnv<T>(key: CustomEnvKey<T>,  value: T)
```

Sets a custom environment variable that can be read by descendant custom components within the scope.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [CustomEnvKey](arkts-arkui-common-comp-customenvkey-c.md)&lt;T&gt; | Yes | Key of the custom environment variable. |
| value | T | Yes | Value of the custom environment variable. The type T of value corresponds to the type T of CustomEnvKey&lt;T&gt;. |

## env

```TypeScript
env<T>(key: WritableSystemEnvKey<T>, value: T)
```

Sets the system environment variable within the scope. The currently officially supported system environment variable keys are **WritableEnvKey.FONT_SCALE** and **WritableEnvKey.DIRECTION**.

> **NOTE:** 
> 
> - `WithEnv.env(WritableEnvKey.FONT_SCALE, value)` provides a local font scale for components within the scope of the trailing closure. `value` is of the number type, indicating the font scale multiplier. If the set `value` is less than 0, it is treated as 0.
> 
> - The effective font scale of components within the scope of the **WithEnv** trailing closure is jointly determined by the value set through the **env** attribute with the key **WritableEnvKey.FONT_SCALE** and the component's own font scale constraints. These constraints can be set through the component's `minFontScale` and `maxFontScale` attributes, or through global configurations such as [fontSizeMaxScale](../../../quick-start/app-configuration-file.md) in the app configuration. The final effective value is the value of **WritableEnvKey.FONT_SCALE** within the range of each constraint.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [WritableSystemEnvKey](arkts-arkui-common-comp-writablesystemenvkey-c.md)&lt;T&gt; | Yes | System environment variable key. Currently, **WritableEnvKey.FONT_SCALE** and **WritableEnvKey.DIRECTION** are officially supported. |
| value | T | Yes | System environment variable value. The type T of **value** corresponds to the type T in **WritableSystemEnvKey&lt;T&gt;**. When `key` is `WritableEnvKey.FONT_SCALE`, the type of `value` is number. When `key` is `WritableEnvKey.DIRECTION`, the type of `value` is Direction. |
