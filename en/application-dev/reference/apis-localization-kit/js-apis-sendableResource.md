# SendableResource

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:25:09.267Z pushedAt=2026-07-17T06:02:25.678Z -->

This module provides information related to `SendableResource`, including the application bundle package name, application module name, and resource type. `SendableResource` implements the [ISendable](../../arkts-utils/arkts-sendable.md#isendable) API
 and supports cross‑thread transmission, enabling access to application resources in multi‑thread scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Import a module.

```js
import { resourceManager } from '@kit.LocalizationKit';
```

## SendableResource

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Global.ResourceManager

| Name        | Type    | Read-Only  | Optional |Description         |
| ---------- | ------ | ----- | ----  | ---------------|
| bundleName | string | No    | No | Application bundle name. |
| moduleName | string | No    | No | Application module name. |
| id         | number | No    | No | Resource ID. The value ranges are as follows:<br/>-&nbsp;Application resource ranges: [0x01000000, 0x06FFFFFF] and [0x08000000, 0xFFFFFFFF], indicating the resource IDs of the application itself.<br/>-&nbsp;System resource range: [0x07000000, 0x07FFFFFF], indicating the resource IDs preset by the system. |
| params     | collections.Array<string \| number> | No    | Yes | Resource parameters, including the resource name (string type), replacement values for formatting APIs (string or number in the order of placeholders), and plural quantifier (number type, indicating the quantity). The replacement value of the formatting API is used for parameter substitution during string formatting, while the quantifier of the plural API is used to select the plural form in multilingual environments.      |
| type       | number | No    | Yes | Resource type. The options are as follows:<br/>-&nbsp;**10001**: color<br/>-&nbsp;**10002**: float<br/>-&nbsp;**10003**: string<br/>-&nbsp;**10004**: plural<br/>-&nbsp;**10005**: boolean<br/>-&nbsp;**10006**: intarray<br/>-&nbsp;**10007**: integer<br/>-&nbsp;**10008**: pattern<br/>-&nbsp;**10009**: strarray<br/>-&nbsp;**20000**: media<br/>-&nbsp;**30000**: rawfile<br/>-&nbsp;**40000**: symbol |