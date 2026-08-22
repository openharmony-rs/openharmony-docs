# 沉浸光感兼容性适配
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

沉浸光感从API版本26.0.0开始支持。应用在接入沉浸式系统材质时，如果还需要兼容低版本，需要处理好两方面问题。一是沉浸式系统材质接口在低版本上不可用，需要进行版本判断。二是组件上已设置的背景色、背景模糊、阴影、边框等样式与材质效果冲突，需要在沉浸式系统材质生效时将这些属性置为undefined，使其恢复默认值，避免遮挡材质效果。

本文从应用级开启和组件级接入两个角度，指导沉浸式系统材质向低版本兼容的适配方案。

## 应用级开启的兼容

应用级开关（[module.json5](../quick-start/module-configuration-file.md)中的"ohos.arkui.UIMaterial.state"配置）仅在应用的[targetAPIVersion](../quick-start/app-configuration-file.md)不低于26.0.0时生效，且仅在entry类型的module中生效。开启应用级开关后，支持应用级开启的组件（完整组件清单请参见[MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)）会默认开启沉浸式系统材质。

此类组件在接入沉浸式系统材质前，通常已经设置了背景色、背景模糊、阴影或边框样式，这些属性与材质效果冲突：不透明的背景色或背景模糊样式会覆盖在材质层之上，导致材质效果被遮挡；DEFAULT模式下主动设置这些属性还会导致沉浸式系统材质不默认开启。

兼容方案：通过[uiMaterial.getMaterialInfo()](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetmaterialinfo)获取[MaterialInfo](../reference/apis-arkui/arkts-apis-uimaterial.md#materialinfo)，根据其中的[MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)判断当前应用级沉浸式系统材质配置是否开启。如果当前组件支持应用级开启且沉浸式系统材质已开启，则需要将与沉浸式系统材质冲突的属性设置为undefined，确保材质效果正常呈现。

```ts
import { uiMaterial } from '@kit.ArkUI';

@Entry
@Component
struct AppLevelCompatibility {
  private info: uiMaterial.MaterialInfo = uiMaterial.getMaterialInfo();

  build() {
    Column() {
      // Select组件支持应用级开启，ENABLE模式下默认开启沉浸式系统材质
      Select([{ value: '选项1' }, { value: '选项2' }])
        .value('选择')
        // 应用级沉浸式系统材质开启时，将冲突属性置为undefined，恢复属性默认值，避免遮挡材质效果
        .backgroundColor(this.info.state === uiMaterial.MaterialState.ENABLE ? undefined : Color.White)
    }
  }
}
```

## 组件级接入的兼容

组件级接入通过[systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)属性为单个组件设置沉浸式系统材质，该属性及[ImmersiveMaterial](../reference/apis-arkui/arkts-apis-uimaterial.md#immersivematerial)类均从API版本26.0.0开始支持，在低版本上不可用。

兼容方案：通过getApiVersion判断应用的targetAPIVersion是否不低于26.0.0，如果是则标记一个flag。当flag为true时，通过systemMaterial设置材质参数，并将其余冲突属性设置为undefined；当flag为false时，保持组件原有的背景色等样式设置，保证低版本上的显示效果。

```ts
import { uiMaterial } from '@kit.ArkUI';
import { deviceInfo } from '@kit.BasicServicesKit';

@Entry
@Component
struct AppLevelCompatibility {
  private info: uiMaterial.MaterialInfo = uiMaterial.getMaterialInfo();

  build() {
    Column() {
      // 针对新版本API单独维护
      if (deviceInfo.sdkApiVersion >= 26) {
        Select([{ value: '选项1' }, { value: '选项2' }])
          .value('选择')
          .systemMaterial(new uiMaterial.ImmersiveMaterial({style: uiMaterial.ImmersiveStyle.THIN}))
      } else {
        // Select组件支持应用级开启，ENABLE模式下默认开启沉浸式系统材质
        Select([{ value: '选项1' }, { value: '选项2' }])
          .value('选择')
          // 应用级沉浸式系统材质开启时，将冲突属性置为undefined，恢复属性默认值，避免遮挡材质效果
          .backgroundColor(Color.White)
      }
      Select([{ value: '选项1' }, { value: '选项2' }])
        .value('选择')
        // 应用级沉浸式系统材质开启时，将冲突属性置为undefined，恢复属性默认值，避免遮挡材质效果
        .systemMaterial(deviceInfo.sdkApiVersion >= 26 ?
          new uiMaterial.ImmersiveMaterial({style: uiMaterial.ImmersiveStyle.THIN}) : undefined)
    }
  }
}
```