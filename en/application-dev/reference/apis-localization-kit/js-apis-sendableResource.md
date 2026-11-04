# SendableResource

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a8446c9be4dbeea364560754c05cf5bc58bb15cf translatedAt=2026-11-03T13:48:46.551Z pushedAt=2026-11-04T08:47:59.752Z nl=1 -->

This module provides information related to SendableResource resources, including the bundle name, module name, resource type, and so on. SendableResource implements the [ISendable](../../arkts-utils/arkts-sendable.md#isendable) interface and supports cross-thread transfer, for accessing application resources in multi-thread scenarios.

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
| bundleName | string | No | No | Bundle name of the application. |
| moduleName | string | No | No | Application module name. |
| id | number | No | No | Resource ID. The value ranges are as follows:<br/>-&nbsp;Application resource range: [0x01000000, 0x06FFFFFF] and [0x08000000, 0xFFFFFFFF], indicating the resource ID of the application itself.<br/>-&nbsp;System resource range: [0x07000000, 0x07FFFFFF], indicating the preset system resource ID. |
| params | collections.Array<string \| number> | No | Yes | Resource parameters, including the resource name (string type), replacement values for the formatting API (string or number provided in placeholder order), and the quantifier for the plural API (number type, indicating the quantity). The replacement values of the formatting API are used for parameter substitution during string formatting, and the quantifier of the plural API is used to select the plural form in a multilingual environment. |
| type | number | No | Yes | Resource type. The values are as follows:<br/>-&nbsp;10001: color<br/>-&nbsp;10002: float<br/>-&nbsp;10003: string<br/>-&nbsp;10004: plural<br/>-&nbsp;10005: boolean<br/>-&nbsp;10006: intarray<br/>-&nbsp;10007: integer<br/>-&nbsp;10008: pattern<br/>-&nbsp;10009: strarray<br/>-&nbsp;20000: media<br/>-&nbsp;30000: rawfile<br/>-&nbsp;40000: symbol |