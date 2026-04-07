# SendableResource

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **SendableResource** module provides sendable resource information, such as the application bundle name, application module name, and resource ID.

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
| bundleName | string | No   | No| Bundle name of the application.|
| moduleName | string | No   | No| Module name of the application.|
| id         | number | No   | No| Resource ID. The value can be:<br>-&nbsp;Application resource range: [0x01000000, 0x06FFFFFF] and [0x08000000, 0xFFFFFFFF]<br>-&nbsp;System resource range: [0x07000000, 0x07FFFFFF]|
| params     | collections.Array<string \| number> | No   | Yes| Other resource parameters, including the resource name, substitution value for the formatting API, and quantifier for the singular-plural formatting API.     |
| type       | number | No   | Yes| Resource type. The options are as follows:<br>-&nbsp;10001: color<br>-&nbsp;10002: float<br>-&nbsp;10003: string<br>-&nbsp;10004: plural<br>-&nbsp;10005: boolean<br>-&nbsp;10006: intarray<br>-&nbsp;10007: integer<br>-&nbsp;10008: pattern<br>-&nbsp;10009: strarray<br>-&nbsp;20000: media<br>-&nbsp;30000: rawfile<br>-&nbsp;40000: symbol|
