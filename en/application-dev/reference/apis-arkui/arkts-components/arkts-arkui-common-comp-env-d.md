# @Env

```TypeScript
declare function Env<T>(key: SystemEnvKey<T> | SystemProperties): PropertyDecorator
```

The **\@Env** decorator is used to obtain system environment variables, helping you sense system environment changes and dynamically adjust the UI display.

Obtains system environment variables. Before API version 26.0.0, only the **SystemProperties** enum can be passed in. Since API version 26.0.0, the [SystemEnvKey&lt;T&gt;](arkts-arkui-common-comp-systemenvkey-c.md) class or the [SystemProperties](arkts-arkui-common-comp-systemproperties-e.md) enum can be passed in as the parameter.

For details about the developer guide, see [\@Env Developer Guide](../../../ui/arkts-env-system-property.md).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare function Env<T>(key: SystemEnvKey<T> | SystemProperties): PropertyDecorator--><!--Device-unnamed-declare function Env<T>(key: SystemEnvKey<T> | SystemProperties): PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
