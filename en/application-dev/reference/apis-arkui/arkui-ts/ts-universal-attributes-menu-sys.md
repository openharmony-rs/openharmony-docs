# Menu Control (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8373999722a4e142b6e04cfa9e8267e53d682e28 translatedAt=2026-11-03T03:24:16.568Z pushedAt=2026-11-13T01:06:00.105Z nl=1 -->

A context menu – a vertical list of items – can be bound to a component and displayed by long-pressing, clicking, or right-clicking the component.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [Menu Control](./ts-universal-attributes-menu.md).

## ContextMenuOptions<sup>10+</sup>

Configures the visual presentation options of the system menu, including the nonlinear animation mode (distortion effect) and the edge light of the menu under the new material, to improve the interactive experience and visual quality of menu display.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| Name                 | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | No | Yes | Sets the nonlinear animation mode of the menu under system materials.<br />**Default value:** DistortionMode.DISTORTION_AUTO <br/>**Since:** 26.0.0 <br />**System API:** This is a system API.|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode)| No | Yes | Sets the edge light animation mode of the menu under system materials.<br />**Default value:** EdgeLightMode.EDGELIGHT_DISABLED <br/>**Since:** 26.0.0 <br />**System API:** This is a system API.|

## Examples

### Example 1: Setting Immersive Material, Distortion, and Edge Light for a Menu

This example uses [bindContextMenu](./ts-universal-attributes-menu.md#bindcontextmenu8) to bind a menu to a component (triggered by a long press or right-click), and uses [ContextMenuOptions](#contextmenuoptions10) to set the system material [systemMaterial](./ts-universal-attributes-menu.md#contextmenuoptions10), as well as the nonlinear deformation [distortionMode](#contextmenuoptions10) and edge light [edgeLightMode](#contextmenuoptions10), both of which are set to **AUTO** mode (taking effect adaptively based on the device computing power tier and the immersive light perception configuration in the system settings).

Since API version 26.0.0, [ContextMenuOptions](#contextmenuoptions10) supports the **distortionMode** and **edgeLightMode** attributes.

```ts
// xxx.ets
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MenuMaterialExample {
  // Immersive material object.
  @State myMaterial: SystemUiMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THICK,
  });

  @Builder MenuBuilder() {
    Menu() {
      MenuItem({ content: 'Menu1' })
        .onClick(() => {
          console.info('handle Menu1 select');
        })
      MenuItem({ content: 'Menu2' })
        .onClick(() => {
          console.info('handle Menu2 select');
        })
    }
  }

  build() {
    Stack() {
      Column() {
        Text('click to show Menu')
          .fontSize(20)
          .margin({ top: 20 })
          .bindMenu(this.MenuBuilder, {
            // Set the immersive material.
            systemMaterial: this.myMaterial,
            // Adapt the distortion.
            distortionMode: DistortionMode.DISTORTION_AUTO,
            // Adapt the edge light.
            edgeLightMode: EdgeLightMode.EDGELIGHT_AUTO,
          })
      }
      .width('100%')
      .height('100%')
      .justifyContent(FlexAlign.Center)
    }
    .backgroundColor(Color.Gray)
  }
}
```

The illustration for this example shows the strong effect on a high-performance device with immersive material, distortion, and edge light enabled.

<!--Del--> <!--DelEnd-->

The illustration for this example shows the strong effect on a high-performance device without immersive material, distortion, and edge light enabled.

<!--Del--> <!--DelEnd-->