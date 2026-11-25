# Custom Dialog Box (CustomDialog) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8373999722a4e142b6e04cfa9e8267e53d682e28 translatedAt=2026-11-03T02:50:29.858Z pushedAt=2026-11-13T01:06:00.029Z nl=1 -->

Displays a custom dialog box through the [CustomDialogController](ts-methods-custom-dialog-box.md#customdialogcontroller) class. When using a dialog box component, prioritize a custom dialog box for easier customization of the dialog box style and content.

> **NOTE**
>
> This API is supported since API version 7. Newly added content in later versions will be marked with a superscript to indicate the starting version.
>
> This page covers only the system APIs of this module. For other public APIs, see [Custom Dialog Box (CustomDialog)](ts-methods-custom-dialog-box.md).

## CustomDialogControllerOptions

Defines the style of the custom dialog box.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                           | Type                                     | Read-Only | Optional | Description                                     |
| ----------------------------- | ---------------------------------------- | ---- | ---------------------------------------- | ---------------------------------------- |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | No | Yes | Distortion animation mode of the dialog box under system materials.<br/>**Default value:** **DistortionMode.DISTORTION_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model.|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | No | Yes | Edge light animation mode of the dialog box under system materials.<br/>**Default value:** **EdgeLightMode.EDGELIGHT_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model. |

## Examples

### Example 1: Setting Immersive Material, Distortion, and Edge Light for a Custom Dialog

This example uses [CustomDialogController](./ts-methods-custom-dialog-box.md#customdialogcontroller) to set the system material **systemMaterial** in [CustomDialogControllerOptions](#customdialogcontrolleroptions), as well as the nonlinear deformation [distortionMode](#customdialogcontrolleroptions) and the light effect [edgeLightMode](#customdialogcontrolleroptions), both of which are set to **AUTO** mode (taking effect adaptively based on the device computing power tier and the immersive light configuration in system settings).

Since API version 26.0.0, [CustomDialogControllerOptions](#customdialogcontrolleroptions) adds the **distortionMode** and **edgeLightMode** attributes.

```ts
import { uiMaterial } from '@kit.ArkUI';

@CustomDialog
struct CustomDialogExample {
  controller: CustomDialogController;

  build() {
    Column() {
      Text('CustomDialog Text').fontSize(20).margin(10)
      Button('OK')
        .margin(10)
        .onClick(() => {
          this.controller.close();
        })
    }
  }
}

@Entry
@Component
struct CustomDialogPage {
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample(),
    alignment: DialogAlignment.Center,
    // Set the immersive material.
    systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK }),
    // Adapt to nonlinear deformation.
    distortionMode: DistortionMode.DISTORTION_AUTO,
    // Adapt to light effects.
    edgeLightMode: EdgeLightMode.EDGELIGHT_AUTO,
  });

  build() {
    Column() {
      Button('CustomDialog')
        .margin(20)
        .onClick(() => {
          if (this.dialogController != null) {
            this.dialogController.open();
          }
        })
    }
    .height('100%')
    .width('100%')
    .backgroundColor(Color.Gray)
  }
}
```

The following figure shows the strong effect on a high-performance device with immersive material, distortion, and edge light configured.

<!--Del--> <!--DelEnd-->

The following figure shows the strong effect on a high-performance device with immersive material, distortion, and edge light configured.

<!--Del--> <!--DelEnd-->