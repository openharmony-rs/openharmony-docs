# Union Effect (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

This section describes how to set the union effect.

> **NOTE:**
>
> - This parameter is supported since API version 23. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs provided by this module are system APIs.

## useUnionEffect

useUnionEffect(value: boolean | undefined): T;

Whether to use the union effect of the ancestor [UnionEffectContainer](ts-container-unioneffectcomponent-sys.md) component as a part of **UnionEffectContainer** for shape union.

If this attribute is not set, the union effect of the ancestor **UnionEffectContainer** component is not used by default.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | boolean \| undefined | Yes| Whether to use the union effect of the ancestor **UnionEffectContainer** component.<br>When **useUnionEffect** is set to **true**, the current component uses the union effect of the ancestor **UnionEffectContainer** component and is considered as a part of the ancestor during shape calculation for the ancestor component.<br>When **useUnionEffect** is set to **false**, the current component does not use the union effect of the ancestor **UnionEffectContainer** component.<br>Setting it to **undefined** restores the default behavior (that is, not using the union effect of the ancestor **UnionEffectContainer** component).|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

**Example**

For details, see [UnionEffectContainer Example](ts-container-unioneffectcomponent-sys.md#example).
