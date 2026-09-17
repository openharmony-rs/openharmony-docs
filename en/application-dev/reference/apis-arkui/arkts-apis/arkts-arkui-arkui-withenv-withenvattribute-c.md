# WithEnvAttribute

Define the WithEnv attribute functions.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { WithEnv, WithEnvAttribute} from '@kit.ArkUI';
```

## customEnv

```TypeScript
customEnv<T>(key: CustomEnvKey<T>,  value: T): WithEnvAttribute
```

Defining Custom Environment Variables

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [CustomEnvKey](../arkts-components/arkts-arkui-customenvkey-c.md)&lt;T&gt; | Yes | Key for custom environment variables. |
| value | T | Yes | Value of custom environment variables. |

**Return value:**

| Type | Description |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | WithEnvAttribute object. |

## env

```TypeScript
env<T>(key: WritableSystemEnvKey<T>, value: T): WithEnvAttribute
```

Defining System Environment Variables

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [WritableSystemEnvKey](../arkts-components/arkts-arkui-writablesystemenvkey-c.md)&lt;T&gt; | Yes | Key for system environment variables. |
| value | T | Yes | Value of system environment variables. |

**Return value:**

| Type | Description |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | WithEnvAttribute object. |
