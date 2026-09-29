# WritableEnvKey

```TypeScript
declare class WritableEnvKey
```

Defines the set of writable system environment variable keys, which are used to obtain the corresponding system environment variables through the **\@Env** decorator. You can use the env method in [WithEnv](arkts-arkui-withenv-comp-attribute.md#withenv) to set local environment variable values to affect the rendering of descendant components. For details, see [Example 2: Setting Local Layout Direction](arkts-arkui-withenv-comp-attribute.md#withenv).

**Since:** 26.0.0

<!--Device-unnamed-declare class WritableEnvKey--><!--Device-unnamed-declare class WritableEnvKey-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DIRECTION

```TypeScript
static readonly DIRECTION: WritableSystemEnvKey<Direction>
```

Variable parameter of [\@Env](arkts-arkui-common-comp-env-d.md#env). The value of the Direction enum can be obtained through **\@Env(WritableEnvKey.DIRECTION)**. <br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md), it is used to obtain the layout direction of the screen where the window is located.

**Type:** [WritableSystemEnvKey](arkts-arkui-common-comp-writablesystemenvkey-c.md)&lt;[Direction](../arkts-apis/arkts-arkui-direction-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-WritableEnvKey-static readonly DIRECTION: WritableSystemEnvKey<Direction>--><!--Device-WritableEnvKey-static readonly DIRECTION: WritableSystemEnvKey<Direction>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FONT_SCALE

```TypeScript
static readonly FONT_SCALE: WritableSystemEnvKey<number>
```

Variable parameter of [\@Env](arkts-arkui-common-comp-env-d.md#env). The value of the number type can be obtained through **\@Env(WritableEnvKey.FONT_SCALE)**. There is no upper limit for the value, and values less than or equal to 0 are processed as 0. <br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md), it is used to provide a local font scale factor for descendant components.

**Type:** [WritableSystemEnvKey](arkts-arkui-common-comp-writablesystemenvkey-c.md)&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-WritableEnvKey-static readonly FONT_SCALE: WritableSystemEnvKey<double>--><!--Device-WritableEnvKey-static readonly FONT_SCALE: WritableSystemEnvKey<double>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
