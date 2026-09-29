# CustomEnvKey

```TypeScript
declare class CustomEnvKey<S>
```

Defines the type of the key for a custom environment variable.

**Since:** 26.0.0

<!--Device-unnamed-declare class CustomEnvKey<S>--><!--Device-unnamed-declare class CustomEnvKey<S>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
protected constructor()
```

Creates an instance of this class.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomEnvKey-protected constructor()--><!--Device-CustomEnvKey-protected constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## create

```TypeScript
static create<T>(): CustomEnvKey<T>
```

Creates a custom environment variable key, which serves as a parameter of the **\@CustomEnv** decorator.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>--><!--Device-CustomEnvKey-static create<T>(): CustomEnvKey<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CustomEnvKey](arkts-arkui-common-comp-customenvkey-c.md)&lt;T&gt; | Custom environment variable key, used to identify the custom environment variable to obtain. |

## type

```TypeScript
private type?: S
```

Type of the key for a custom environment variable.

**Type:** S

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomEnvKey-private type?: S--><!--Device-CustomEnvKey-private type?: S-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
