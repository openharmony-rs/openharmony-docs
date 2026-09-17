# Constants (System API)

## audioBalance

```TypeScript
const audioBalance: Config<number>
```

Indicates the configuration for left and right channel volume balance. **-1.0** indicates output from the left channel only; **0.0** indicates balanced output from both channels; **1.0** indicates output from the right channel only. Intermediate values represent a linear ratio of the left and right channel volumes. The value ranges from -1.0 to 1.0. The default value is **0.0**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**Since:** 10

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## audioMono

```TypeScript
const audioMono: Config<boolean>
```

Indicates the mono audio feature status. The value **true** indicates that the mono audio feature is enabled, and **false** indicates that it is disabled. The default value is **false**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 10

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## clickResponseTime

```TypeScript
const clickResponseTime: Config<ClickResponseTime>
```

Length of time required for a click.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[ClickResponseTime](arkts-accessibility-config-clickresponsetime-t-sys.md)&gt;

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## daltonizationState

```TypeScript
const daltonizationState: Config<boolean>
```

Indicates the color correction feature status. Used together with daltonizationColorFilter. The value **true** indicates that color correction is enabled, and **false** indicates that it is disabled. The default value is **false**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## ignoreRepeatClick

```TypeScript
const ignoreRepeatClick: Config<boolean>
```

Whether to ignore repeated clicks. This parameter must be used together with **repeatClickInterval**. The value **true** indicates that the feature of ignoring repeated clicks is enabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## repeatClickInterval

```TypeScript
const repeatClickInterval: Config<RepeatClickInterval>
```

Indicates the configuration for the interval of ignoring repeated clicks. Used together with ignoreRepeatClick. This configuration takes effect only when ignoreRepeatClick is set to **true**. The default value is Shortest, indicating the shortest interval.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[RepeatClickInterval](arkts-accessibility-config-repeatclickinterval-t-sys.md)&gt;

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## screenMagnification

```TypeScript
const screenMagnification: Config<boolean>
```

Indicates the configuration of screen magnification.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## shortkeyMultiTargets

```TypeScript
const shortkeyMultiTargets: Config<Array<string>>
```

Indicates the multi-target list configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format ['bundleName/abilityName']. If the format is incorrect or the name is invalid, the setting does not take effect.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;Array&lt;string&gt;&gt;

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
