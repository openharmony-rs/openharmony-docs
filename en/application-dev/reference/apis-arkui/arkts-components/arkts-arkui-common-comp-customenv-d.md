# @CustomEnv

```TypeScript
declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator
```

This component is used to obtain custom environment variables.

See the developer guide: [\@CustomEnv: Custom Environment Variable](../../../ui/arkts-custom-env-property.md).

Obtains custom environment variables. A custom environment variable key is created through [CustomEnvKey.create()](arkts-arkui-common-comp-customenvkey-c.md#create) and passed as a parameter to the **\@CustomEnv** decorator.

A variable decorated by **\@CustomEnv** reads the environment variable value corresponding to the key. If the environment variable is not set, the locally declared default value is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator--><!--Device-unnamed-declare function CustomEnv<T>(key: CustomEnvKey<T>): PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
