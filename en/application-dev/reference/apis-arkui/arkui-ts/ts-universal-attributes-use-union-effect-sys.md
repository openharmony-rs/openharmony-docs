# Union Effect (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-09-02T12:14:10.822Z -->

This module describes how to set and use the union effect. The union effect means that multiple child components undergo shape union in the UnionEffectContainer container to form a unified visual fusion form.

> **NOTE**
>
> - This module is supported since API version 23. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs provided by this module are system APIs.

## useUnionEffect

useUnionEffect(value: boolean \| undefined): T

Whether to use the union effect of the ancestor [UnionEffectContainer](ts-container-unioneffectcomponent-sys.md) component, that is, whether to serve as a part of UnionEffectContainer for shape union and participate in the fusion form calculation.

When not set, the union effect of the ancestor UnionEffectContainer component is not used by default.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | Yes | Whether to use the fusion effect of the ancestor component UnionEffectContainer.<br>When the value is true, the current component uses the fusion effect of the ancestor component UnionEffectContainer and is treated as part of the UnionEffectContainer when the ancestor component UnionEffectContainer calculates the shape. If the current component has no ancestor UnionEffectContainer, setting useUnionEffect to true does not produce a fusion effect.<br>When the value is false, the current component does not use the fusion effect of the ancestor component UnionEffectContainer.<br>When set to undefined, the current component restores to not using the fusion effect of the ancestor component UnionEffectContainer.|

**Return value**

| Type | Description |
| -------- | -------- |
| T | Current component, used for chained calls. |

## useUnionEffect

useUnionEffect(value: boolean \| undefined, options?: GravityCenterOptions): T

Whether to use the union effect of the ancestor [UnionEffectContainer](ts-container-unioneffectcomponent-sys.md) component, that is, whether to serve as a part of UnionEffectContainer for shape union and participate in the fusion form calculation. When no ancestor UnionEffectContainer component exists, setting this attribute has no effect.

When not set, the union effect of the ancestor UnionEffectContainer component is not used by default.

> **NOTE**
>
> When this API is called multiple times with the [GravityCenterOptions](#gravitycenteroptions) parameter, only the gravity center parameter set last takes effect.

**Since**: 26.0.0

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | Yes | Whether to use the fusion effect of the ancestor component UnionEffectContainer.<br>When the value is true, the current component uses the fusion effect of the ancestor component UnionEffectContainer, and is treated as part of the UnionEffectContainer when the ancestor component UnionEffectContainer computes the shape. If the current component has no ancestor UnionEffectContainer, the value true does not produce a fusion effect.<br>When the value is false, the current component does not use the fusion effect of the ancestor component UnionEffectContainer.<br>When set to undefined, the current component restores to not using the fusion effect of the ancestor component UnionEffectContainer.|
| options | [GravityCenterOptions](#gravitycenteroptions) | No | Center of gravity parameter.<br>When not set, the center of gravity feature is not enabled.<br>**NOTE**<br>This parameter must be used together with [unionMode](./ts-container-unioneffectcomponent-sys.md#unionmode), and unionMode must be UnionMode.GRAVITY_UNION, and value must be true for it to take effect. It does not take effect when set alone or when the prerequisites are not met.      |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## GravityCenterOptions

Defines the gravity center parameter.

> **NOTE**
>
> This parameter must be used together with [unionMode](./ts-container-unioneffectcomponent-sys.md#unionmode), and unionMode must be UnionMode.GRAVITY_UNION, and the value of useUnionEffect must be true for it to take effect. It does not take effect when set alone.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name               | Type                              | Read-only | Optional | Description                                                    |
| ------------------ | -------------------------------- | ---- | ---- |------------------------------------------------------- |
| gravityCenter      | boolean                          | No   | Yes   | Specifies whether the current component is the center of gravity.<br>The value true indicates that the current component is the center of gravity, and false indicates the opposite.<br>Default value: false                                           |
| gravityIntensity   | number                           | No   | Yes   | Defines the intensity of the attraction or repulsion at the center of gravity.<br>Takes effect only when gravityCenter is true.<br>Default value: 0<br>A negative value indicates repulsion, and a positive value indicates attraction. |

**Example**

For details, see [UnionEffectContainer Example](ts-container-unioneffectcomponent-sys.md#examples).
