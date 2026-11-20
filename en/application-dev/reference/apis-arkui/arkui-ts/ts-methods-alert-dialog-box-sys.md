# Alert Dialog Box (AlertDialog) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8373999722a4e142b6e04cfa9e8267e53d682e28 translatedAt=2026-11-03T02:48:20.821Z pushedAt=2026-11-13T01:06:00.024Z nl=1 -->

Displays an alert dialog box component with configurable text content and response callbacks.

> **NOTE**
>
> This feature is supported since API version 7. Newly added content in later versions will be marked with a superscript to indicate the initial version.
>
> This module depends on the UI execution context and cannot be used where the [UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). See [UIContext](../arkts-apis-uicontext-uicontext.md) for details.
>
> This page covers only the system APIs of this module. For other public APIs, see [Alert Dialog Box (AlertDialog)](ts-methods-alert-dialog-box.md).

## AlertDialogParam

Defines the configuration parameters of the alert dialog box.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                              | Type                                                         | Read-Only | Optional | Description                                                        |
| --------------------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | No | Yes | Distortion animation mode of the dialog box under system materials.<br/>**Default value:** **DistortionMode.DISTORTION_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model.|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | No | Yes | Edge light animation mode of the dialog box under system materials.<br/>**Default value:** **EdgeLightMode.EDGELIGHT_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model. |

## Examples

### Example 1: Setting Immersive Material, Distortion and Edge Light for an Alert Dialog

This example uses [showAlertDialog](../arkts-apis-uicontext-uicontext.md#showalertdialog) to set the system material **systemMaterial** in [AlertDialogParam](#alertdialogparam), as well as the nonlinear shape [distortionMode](#alertdialogparam) and streaming light [edgeLightMode](#alertdialogparam), both of which are set to **AUTO** mode (which takes effect adaptively based on the device computing capability tier and the immersive light-sensing configuration in system settings).

Since API version 26.0.0, [AlertDialogParam](#alertdialogparam) has added the **distortionMode** and **edgeLightMode** attributes.

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct AlertDialogExample {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      Column() {
        Button("AlertDialog")
          .margin(20)
          .onClick(() => {
            this.getUIContext().showAlertDialog({
              title: 'AlertDialog Title',
              message: 'AlertDialog Text',
              primaryButton: {
                value: 'OK',
                action: () => {
                  console.info('primaryButton');
                }
              },
              secondaryButton: {
                value: 'Cancel',
                action: () => {
                  console.info('secondaryButton');
                }
              },
              // Set the immersive material.
              systemMaterial: new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.ULTRA_THICK }),
              // Adapt to distortion.
              distortionMode: DistortionMode.DISTORTION_AUTO,
              // Adapt to edge light.
              edgeLightMode: EdgeLightMode.EDGELIGHT_AUTO,
            });
          })
      }
      .height('100%')
      .width('100%')
      .backgroundColor(Color.Gray)
    }
  }
}
```

The following figure shows the strong effect on a high-performance device with immersive material, distortion and edge light enabled.

<!--Del--> <!--DelEnd-->

The following figure shows the strong effect on a high-performance device without immersive material, distortion and edge light enabled.

<!--Del--> <!--DelEnd-->