# @ohos.arkui.dialog (Dialog Box) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=53d1db0ac48b34f221cb3bd2e42b7bdd28d186df translatedAt=2026-11-11T09:22:39.347Z pushedAt=2026-11-12T03:29:11.239Z nl=1 -->

A dialog box is one of the important ways for an application to interact with users. It is used to display prompt information, or obtain user confirmation or selection in key operation scenarios. This module provides unified `Dialog` type declarations, including dialog box options, button configuration, worksheet items, and enums such as the dialog box controller, alignment mode, and state. To call specific APIs, use the [DialogPresenter](arkts-apis-uicontext-dialogpresenter.md) object in `UIContext`.

> **NOTE**
>
> This topic contains only the system APIs of this module. For other public APIs, see [@ohos.arkui.dialog (Dialog Box)](js-apis-dialog.md).

**Since**: 26.0.1

## Modules to Import

```ts
import { dialog } from '@kit.ArkUI';
```

## DialogBaseOptions

Provides basic options shared by all dialog boxes, defining common attributes such as the background, border, alignment, mask, and avoidance of a dialog box. This section lists only the system API attributes. For other public attributes, see [DialogBaseOptions](js-apis-dialog.md#dialogbaseoptions).

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                                         | Read-Only | Optional | Description                                                  |
| -------------- | ------------------------------------------------------------ | --------- | -------- | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | No   | Yes  | Nonlinear animation mode of the dialog box under the system material.<br/>Default value: **DistortionMode.DISTORTION_AUTO**<br/>**System API:** This is a system API. |
| edgeLightMode  | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | No   | Yes  | Edge light animation mode of the dialog box under the system material.<br/>Default value: **EdgeLightMode.EDGELIGHT_AUTO**<br/>**System API:** This is a system API. |

