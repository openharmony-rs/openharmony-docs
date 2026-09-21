# @ohos.arkui.uiMaterial(System Material)

This module provides APIs for system materials. Different system materials correspond to different UI effects, including the background color ([backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor)), border color ([borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor)), border width ([borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth)), and shadow ([shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow)).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) | Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified. |
| [getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md) | Obtains the material configuration information of this application. The returned configuration information comes from the metadata configured in the [module.json5](../../../quick-start/module-configuration-file.md) file of the application. |
| [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) | Check whether [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) is supported on the current device. If it is true, the ImmersiveMaterial object can be used in the [systemMaterial](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#systemmaterial) attribute. If it is false, setting the ImmersiveMaterial object in the systemMaterial attribute will not take effect. It is defined by the device and cannot be modified. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md) | Convert from ImmersiveMaterial to another ImmersiveMaterial set on EffectComponent. |
| [convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md) | Convert from ImmersiveMaterial to another ImmersiveMaterial set on sub component of EffectComponent. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | Immersive material class, which inherits from [Material](arkts-arkui-uimaterial-materialtype-e.md). |
| [Material](arkts-arkui-uimaterial-material-c.md) | System material object on the UI. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Material](arkts-arkui-uimaterial-material-c-sys.md) | System material object on the UI. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | Immersive material parameters. |
| [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) | Provides the light sensing interaction feedback configuration for immersive materials. The configuration is used to customize the color of the light sensing feedback. |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | Provides material configuration information, including the material enabling state and material type. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | System material options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md) | Enumerates immersive material styles. Different material styles correspond to different material parameters, including the blur degree and brightness. |
| [MaterialLevel](arkts-arkui-uimaterial-materiallevel-e.md) | Enumerates the material levels, which indicate the computing power level of the device. Use [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) to obtain the material level of the current device. |
| [MaterialState](arkts-arkui-uimaterial-materialstate-e.md) | Enumerates the material enabling states, indicating the states of the application-level immersive system material configuration. |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e.md) | Enumerates system material types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e-sys.md) | Enumerates immersive material styles. Different material styles correspond to different material parameters, including the blur degree and brightness. |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e-sys.md) | Enumerates system material types. |
<!--DelEnd-->

## Examples

### Example 1: Setting the System Material

This example shows how to apply the Material object of a semi-transparent material to a component using the [systemMaterial](../arkui-ts/ts-universal-attributes-image-effect-sys.md#systemmaterial23) attribute.



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SystemMaterialPage {
  build() {
    Column() {
      Stack() {
        Image($r('app.media.bg1')) // Replace $r('app.media.bg1') with the image resource file you use.
          .width('100%')
          .height('100%')

        Column()
          .width(100)
          .height(50)
          .position({ x: 50, y: 350 })
          .systemMaterial(new uiMaterial.Material({ type: uiMaterial.MaterialType.SEMI_TRANSPARENT })) // Use the semi-transparent system material effect.
      }
      .height('90%')
      .width('90%')
    }
    .height('100%')
    .width('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

### Example 2 (Setting the System Material Using EffectComponent)

This example shows how to set [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) on [EffectComponent](../arkui-ts/ts-container-effectcomponent-sys.md) and its child components, including directly using EC-style materials and applying the materials after conversion through [uiMaterial.convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md) and [uiMaterial.convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md).

Since API version 26.0.0, the uiMaterial.convertToECMaterial and uiMaterial.convertToECSubMaterial APIs are added.

```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State myMaterialBase: uiMaterial.ImmersiveMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
  });
  @State myMaterialEC: uiMaterial.ImmersiveMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN_EC,
  });
  @State myMaterialECSub: uiMaterial.ImmersiveMaterial | undefined = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN_EC_SUB,
  });

  build() {
    Stack() {
      // Replace $r('app.media.startIcon') with the actual resource file.
      Image($r('app.media.startIcon'))
      Row() {
        // It is recommended to use different styles to set materials for EffectComponent and its child components.
        EffectComponent() {
          Row() {
            Column()
              .width(100)
              .height(100)
              .systemMaterial(this.myMaterialECSub)
              .margin(5)
          }
        }
        .systemMaterial(this.myMaterialEC)

        EffectComponent() {
          Row() {
            Column()
              .width(100)
              .height(100)
              .systemMaterial(uiMaterial.convertToECSubMaterial(this.myMaterialBase))
              .margin(5)

            Column()
              .width(100)
              .height(100)
              .systemMaterial(uiMaterial.convertToECSubMaterial(this.myMaterialBase))
              .margin(5)
          }
        }
        .systemMaterial(uiMaterial.convertToECMaterial(this.myMaterialBase))
      }.height('100%').width('100%').justifyContent(FlexAlign.Center)
    }
  }
}
```

### Example 1: Configuring the Immersive System Material

This example shows how to set the [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) object to a component through [systemMaterial](../arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial).

Since API version 26.0.0, the ImmersiveMaterial object and systemMaterial attribute are added.

Performance on devices with low-level computing power that support immersive materials



Performance on devices with medium-level computing power that support immersive materials



Performance on devices with high-level computing power that support immersive materials



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct SystemMaterialPage {

  build() {
    Column() {
      Stack() {
        Image($r('app.media.bg1')) // Replace $r('app.media.bg1') with the image resource file you use.
          .width('100%')
          .height('100%')

        Column({ space: 30 }) {
          Column() {
            Text('ULTRA_THIN')
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          }))

          Column() {
            Text('THIN')
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THIN,
          }))

          Column() {
            Text('REGULAR')
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.REGULAR,
          }))

          Column() {
            Text('THICK')
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.THICK,
          }))

          Column() {
            Text('ULTRA_THICK')
          }
          .width(328)
          .height(56)
          .borderRadius(28)
          .justifyContent(FlexAlign.Center)
          .alignItems(HorizontalAlign.Center)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THICK,
          }))
        }
      }
      .height('90%')
      .width('90%')
    }
    .height('100%')
    .width('100%')
    .alignItems(HorizontalAlign.Center)
    .justifyContent(FlexAlign.Center)
  }
}
```

### Example 2: Obtaining Material Configuration Information and Using an Empty Material to Disable the Immersive System Material

This example shows how to use [uiMaterial.getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md) to obtain the material configuration information of this application and use empty to disable the immersive system material effect for a specific component based on the set state.

Since API version 26.0.0, the uiMaterial.getMaterialInfo and empty APIs are added.

Configure the toggle information in the [module.json5](../../../quick-start/module-configuration-file.md) file. Note that the configuration takes effect only in the module of the entry type.

```TypeScript
{
  "module": {
    // ···
    "type": "entry", // Note that the configuration takes effect only in the module of the entry type.
    // ···
    "metadata": [{
      "name": "ohos.arkui.UIMaterial.state",
      "value": "enable"
    }],
    // ···
  }
}
```

Write the sample code as follows:

Performance on devices with high-level computing power that support immersive materials



Performance on devices with medium-level computing power that support immersive materials



Performance on devices with low-level computing power that support immersive materials



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialInfoPage {
  // Obtain the material configuration.
  private info: uiMaterial.MaterialInfo = uiMaterial.getMaterialInfo();
  build() {
    Column() {
      Text(`MaterialState: ${this.info.state}`)
        .fontSize(16)
        .margin({ bottom: 10 })
      Text(`MaterialType: ${this.info.type}`)
        .fontSize(16)
        .margin({ bottom: 20 })

      // Determine the component behavior based on the state.
      if (this.info.state === uiMaterial.MaterialState.ENABLE) {
        // Proactively use the immersive material.
        Button('Enable UiMaterial')
          .backgroundColor(Color.Transparent)
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.ULTRA_THIN
          }))
          .fontColor(Color.Blue)
          .margin({ bottom: 10 })
        // The immersive system material is enabled by default for the Select component.
        Select([
          {value: 'select item'}
        ]).value('select item')
        .margin({ bottom: 10 })
        // Disable the immersive system material for the Select component.
        Select([
          {value: 'select item'}
        ]).value('select item')
        .systemMaterial(uiMaterial.Material.empty)
      }
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    // Replace $r('app.media.img') with the image resource file you use.
    .backgroundImage($r('app.media.img'))
    .backgroundImageSize(ImageSize.FILL)
  }
}
```

### Example 3: Setting an Interactive Deformation Effect for the Component Material

This example shows how to use the interactive API in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) to implement an interactive deformation effect for a component.

Since API version 26.0.0, the interactive API is added.



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Stack() {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      Image($r('app.media.startIcon'))
      Column() {
        Column() {
          Text('Context')
        }
        .margin({ bottom: 100 })
        .width(248)
        .height(56)
        .borderRadius(28)
        .justifyContent(FlexAlign.Center)
        .alignItems(HorizontalAlign.Center)
        .systemMaterial(new uiMaterial.ImmersiveMaterial({
          style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
          interactive: true,
        }))
      }.height('100%').width('100%').justifyContent(FlexAlign.Center)
    }
  }
}
```

### Example 4: Setting a Light Sensing Interaction Feedback Effect for the Component Material

This example shows how to use the lightEffect API in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) to implement a light sensing interaction feedback effect for a component.

Since API version 26.0.0, the lightEffect API is added.



```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct LightEffect {
  @State itemsKey: number[] = [0, 1, 2];
  @State circleRadius: number = 40;
  @State spaceValue: number = 10;
  // Create an immersive material object, and enable interactive deformation and sensory interaction feedback effects (the default white light color is used when lightEffect.color is undefined).
  @State myMaterial: uiMaterial.Material = new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
    interactive: true,
    lightEffect: { color: undefined },
  });

  build() {
    Column() {
      Row() {
        Row({ space: this.spaceValue }) {
          ForEach(this.itemsKey, (_: number, __: number) => {
            Row()
              .width(this.circleRadius * 2)
              .height(this.circleRadius * 2)
              .borderRadius(this.circleRadius)
              .systemMaterial(this.myMaterial)
          })
        }
      }
      .justifyContent(FlexAlign.End)
      .backgroundColor(Color.Black)
      .width('100%')
      .padding(20)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 5: Querying the Material Level and Whether Immersive Materials Are Supported

This example describes how to use [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) to obtain the material level of a device and use [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) to check whether the device supports immersive materials. Based on the result, you can determine whether to set immersive materials for components. With this adaptation method, the application can reuse the same set of code on devices that support immersive materials and those that do not. On devices that do not support immersive materials, the application falls back to the common style, eliminating the need to write different code for different devices.

getGlobalMaterialLevel and isImmersiveMaterialSupported are added since API version 26.0.0.

```TypeScript
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct MaterialLevelPage {
  private materialLevel: uiMaterial.MaterialLevel = uiMaterial.getGlobalMaterialLevel(); // The material level is determined by the device and does not change after the application is running.
  private isSupported: boolean = uiMaterial.isImmersiveMaterialSupported(); // Whether immersive materials are supported is determined by the device and does not change after the application is running.

  build() {
    Column({ space: 20 }) {
      Text(`MaterialLevel: ${this.materialLevel}`)
        .fontSize(16)

      Text(`IsImmersiveMaterialSupported: ${this.isSupported}`)
        .fontSize(16)

      Column({ space: 20 }) {
        // Adaptation mode 1: Check whether the device supports materials and set different attributes based on the support status. This method is more intuitive and applicable to a wider range of attributes.
        Column()
          .width(328)
          .height(56)
          .borderRadius(28)
          .backgroundColor(this.isSupported ? Color.Transparent :
            '#f2f1f3f5') // If the background color is set before systemMaterial, the background color effect contained in the immersive material takes effect on low-computing devices that support immersive materials.
          // On devices that support immersive materials, set a transparent background color and an immersive material. The immersive material takes effect if it is set later. On devices that do not support immersive materials, set the background color to '#f2f1f3f5' and the material effect to undefined. The background color '#f2f1f3f5' takes effect.
          .systemMaterial(this.isSupported ? new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.REGULAR,
          }) : undefined)

        Column()
          .width(328)
          .height(56)
          .borderRadius(28)
          .backgroundColor(this.isSupported ? Color.Transparent :
            $r('sys.color.comp_background_emphasize')) // If the background color is set before systemMaterial, the background color effect contained in the immersive material takes effect on low-computing devices that support immersive materials.
          // On devices that support immersive materials, set a transparent background color and an immersive material with color filling. The immersive material with color filling takes effect if it is set later. On devices that do not support immersive materials, set the background color to a resource value and the material effect to undefined. The background color specified by the resource value takes effect.
          .systemMaterial(this.isSupported ? new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.REGULAR,
            materialColor: $r('sys.color.comp_background_emphasize'),
          }) : undefined)

        // Adaptation mode 2: Set the systemMaterial attribute later and use the feature that systemMaterial can overwrite the attributes that conflict with the material.
        Column()
          .width(328)
          .height(56)
          .borderRadius(28)
          .backgroundColor($r('sys.color.comp_background_emphasize')) // If the background color is set before systemMaterial, the background color effect contained in the immersive material takes effect on low-computing devices that support immersive materials.
          // On high- or medium-computing devices that support immersive materials, the immersive material set later will clear the background color and make it transparent. On low-computing devices that support immersive materials, the background color effect contained in the immersive material set later will overwrite the **backgroundColor** attribute, and the material color will be used.
          // On devices that do not support immersive materials, setting systemMaterial has no effect, and the background color attribute with the resource value takes effect.
          .systemMaterial(new uiMaterial.ImmersiveMaterial({
            style: uiMaterial.ImmersiveStyle.REGULAR,
            materialColor: $r('sys.color.comp_background_emphasize')
          }))
      }
      .backgroundImage($r('app.media.bg1')) // Replace $r("app.media.bg1") with the image resource file you use.
      .backgroundImageSize({ width: '100%', height: '100%' })
      .width('90%')
      .height(300)
      .justifyContent(FlexAlign.Center)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```
