# Built-in Environment Variables

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b7c9d17bef7d70b4a25b2a21b9205c96e03b913a translatedAt=2026-09-02T11:20:34.564Z pushedAt=2026-09-03T01:19:18.866Z -->

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

Built-in environment variables are used to reflect the system environment status. You can query built-in environment variables (such as the color mode and layout direction) through [Environment](./ts-state-management.md#environment).

## ColorMode

Enumerates system color modes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value  | Description      |
| ----- | ---- | ---------- |
| LIGHT | 0    | Light mode.|
| DARK  | 1    | Dark mode.|


## LayoutDirection

Enumerates system layout directions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value  | Description                |
| ---- | ---- | -------------------- |
| LTR  | 0    | Left-to-right layout.      |
| RTL  | 1    | Right-to-left layout.      |
| Auto<sup>8+</sup> | 2    | Automatic layout direction based on the system.|
