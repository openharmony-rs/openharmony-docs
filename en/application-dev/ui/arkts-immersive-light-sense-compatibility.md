# Immersive Light Sense Compatibility Adaptation
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=972f1649fdb6ebd99757019463fe43a902cdae45 translatedAt=2026-08-31T03:04:29.524Z pushedAt=2026-09-01T04:01:53.684Z -->

Immersive Light Sense is supported from API version 26.0.0. When integrating Immersive Light Sense, if you need to be compatible with earlier versions, you must handle two issues. First, when enabling it at the application level, avoid conflicts with immersive system material properties. Second, when enabling it at the component level, the immersive system material APIs are unavailable on earlier versions, so you must perform a version check and set the material to `empty` on earlier versions to explicitly clear the material effect and preserve the component's original style.

This topic provides compatibility adaptation solutions for the immersive system material on earlier versions from two dimensions: application-level enablement and component-level enablement.

## Compatibility Adaptation Solution for Application-level Enablement

When the application-level switch is configured to `default` or `enable` mode, components that support application-level enablement enable the immersive system material by default. Before a component integrates the immersive system material, it usually has styles such as background color, background blur, shadow, or border already set. These properties conflict with the material effect (for details, see [ImmersiveMaterial](../reference/apis-arkui/arkts-apis-uimaterial.md#immersivematerial)). For example, an opaque background color blocks the material effect, preventing the material from being displayed properly.

**Compatibility adaptation solution:**

Call [uiMaterial.getMaterialInfo()](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetmaterialinfo) to obtain the material configuration information [MaterialInfo](../reference/apis-arkui/arkts-apis-uimaterial.md#materialinfo) of the application, and determine whether the application-level immersive system material is enabled based on [MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate). If the component supports application-level enablement and the immersive system material is enabled, clear the properties that conflict with the material to restore their default values, ensuring that the material effect is displayed properly.

**Example:**

The following example uses the `Select` component, which supports application-level enablement, as an example. This component enables the immersive system material by default in `ENABLE` mode. After obtaining the material configuration information through `uiMaterial.getMaterialInfo()`, when the state is `ENABLE` (that is, the immersive system material is enabled), set `backgroundColor` to `undefined` to prevent the white background from blocking the material effect; otherwise, keep the `Color.White` background to ensure the display effect when the material is not enabled.

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct AppLevelCompatibility {
  private info: uiMaterial.MaterialInfo = uiMaterial.getMaterialInfo();

  build() {
    Stack({ alignContent: Alignment.Top }) {
      Column() {}
        .width('100%')
        .height('100%')
        // Replace $r('app.media.invert') with the image resource file required by the developer.
        .backgroundImage($r('app.media.invert'))

      Column() {
        Select([{ value: 'Option 1' }, { value: 'Option 2' }])
          .value('Select')
          // When the application-level immersive system material is enabled, set backgroundColor to undefined to avoid blocking the material effect.
          .backgroundColor(this.info.state === uiMaterial.MaterialState.ENABLE ? undefined :  Color.White)
      }
      .width(100)
      .height(100)
      .justifyContent(FlexAlign.Center)
    }
  }
}
```

In application-level ENABLE mode, Select presents the immersive system material style:

<!--Del--> <!--DelEnd-->

In application-level non-ENABLE mode, the Select button background is white, presenting the default style:

<!--Del--> <!--DelEnd-->

## Component-level Enablement Compatibility Adaptation Solution

Component-level enablement sets the immersive system material for a single component through the [systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial) attribute. Both this attribute and the [ImmersiveMaterial](../reference/apis-arkui/arkts-apis-uimaterial.md#immersivematerial) class are supported starting from API version 26.0.0 and are unavailable on lower versions.

**Compatibility adaptation solution:**

Use `deviceInfo.sdkApiVersion` provided by [@ohos.deviceInfo (Device Information)](../reference/apis-basic-services-kit/js-apis-device-info.md) to determine whether the system software API version is not lower than API version 26.0.0. If the version is not lower than 26.0.0, set the `ImmersiveMaterial` material for the component through `systemMaterial`. If the version is lower than 26.0.0, set `systemMaterial` to [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty) to explicitly clear the material effect, so that the component retains its original style settings such as the background color and ensures the display effect on lower versions.

**Example:**

The following uses the `Select` component as an example to determine the system software API version through `deviceInfo.sdkApiVersion`: if the version is not lower than 26.0.0, set `ImmersiveMaterial` with the material style `THIN` for the component; if the version is lower than 26.0.0, set `systemMaterial` to `undefined`, and the component restores its original style.

```ts
import { uiMaterial } from '@kit.ArkUI';
import { deviceInfo } from '@kit.BasicServicesKit';

@Entry
@Component
struct ComponentLevelCompatibility {
  build() {
    Stack({ alignContent: Alignment.Top }) {
      // Replace $r('app.media.invert') with the image resource file you need.
      Column() {}
        .width('100%')
        .height('100%')
        .backgroundImage($r('app.media.invert'))

      Column() {
        Select([{ value: 'Option 1' }, { value: 'Option 2' }])
          .value('Select')
          // When the API version is not lower than 26.0.0, set the immersive system material; when it is lower than 26.0.0, set it to undefined so that the component restores its original style.
          .systemMaterial(deviceInfo.sdkApiVersion >= 26 ?
            new uiMaterial.ImmersiveMaterial({ style: uiMaterial.ImmersiveStyle.THIN }) : undefined)
      }
      .width(100)
      .height(100)
      .justifyContent(FlexAlign.Center)
    }
  }
}
```

When the system software API version is lower than 26.0.0, the component retains its original style.

<!--Del--> <!--DelEnd-->

When the system software API version is 26.0.0 or later, the component presents the immersive system material effect.

<!--Del--> <!--DelEnd-->