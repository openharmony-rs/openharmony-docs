# 开启沉浸光感
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

沉浸光感提供默认开启、应用级开启和组件级开启三种方式，可按需选择。沉浸光感开启后，效果由材质滤镜、折射、高光、阴影等多层叠加而成，需要大量GPU资源，具体的使用指导请参考[沉浸光感功耗优化](arkts-immersive-light-sense-constraints.md)，其余开启后的常见问题请参考[沉浸光感常见问题](arkts-immersive-light-sense-faq.md)。

## 沉浸光感开启方式对比
> **说明：**
>
> - 开启后，不同组件的效果详见[组件适配沉浸光感](./arkts-immersive-light-sense-component-adaptation.md)。
> - 开启沉浸光感，要确保应用的[targetAPIVersion](../quick-start/app-configuration-file.md)不低于26.0.0。如果低版本适配，适配指导请参考[沉浸光感兼容性适配](arkts-immersive-light-sense-compatibility.md)。
> - 沉浸光感开启后，除了Slider、Toggle以及弹窗类组件，其他组件仅在以下子树中生效：Navigation/NavDestination标题栏子树，或横向Tabs中barPosition为BarPosition.End的底部TabBar子树中。弹窗类组件包括：Popup、Tips、Menu、Sheet、AlertDialog、CustomDialog、ActionSheet、CalendarPickerDialog、DatePickerDialog、TextPickerDialog、TimePickerDialog、Toast、Select下拉菜单、AlphabetIndexer气泡弹窗、SelectionMenu文本选择菜单。

不同开启方式对比如下：

| 开启方式 | 支持的组件 | 说明 |
| --- | --- | --- |
| 默认开启 | [弹出框（Dialog）](arkts-base-dialog-overview.md)、[AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)、[SelectionMenu](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md)、[即时反馈（Toast）](arkts-create-toast.md) | 应用从API版本26.0.0之前升级至API版本26.0.0及以上，在未主动设置沉浸光感的情况下，组件默认开启沉浸光感，无需任何配置。|
| 应用级开启 | 组件清单详见[MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)。 | 通过[module.json5](../quick-start/module-configuration-file.md)统一配置，为支持沉浸光感的组件，批量开启或全局禁用沉浸光感，具体开启方法请参考表格下方内容。|
| 组件级开启 | 支持设置沉浸式系统材质的组件 | 支持通过如下三种方式开启：<br/> 1. 通过通用属性[systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)设置。<br/>2. 弹窗类组件通过options参数中的systemMaterial字段设置。<br/>3. 组件专属接口设置，当前支持设置的组件包括：Select下拉菜单的[menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)、Navigation标题栏的[systemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationtitleoptions11)。 |

应用级开启通过配置文件统一设置应用的沉浸光感开关。在[module.json5](../quick-start/module-configuration-file.md)中，配置[metadata](../quick-start/module-configuration-file.md#metadata标签)参数的name字段配置为"ohos.arkui.UIMaterial.state"，value字段可以为default、enable和disable。该配置仅在entry类型的module中生效。

以下示例展示如何在[module.json5](../quick-start/module-configuration-file.md)中配置enable模式：

<!-- @[MaterialStateConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ImmersiveLightSense/entry/src/main/module.json5) -->

```json5
{
  "module": {
    "name": "entry",
    "type": "entry",
    // ...
    "metadata": [{
      "name": "ohos.arkui.UIMaterial.state",
      "value": "enable"
    }],
    // ...
  }
}
```

开发者可以通过[uiMaterial.getMaterialInfo()](../reference/apis-arkui/arkts-apis-uimaterial.md#uimaterialgetmaterialinfo)获取当前应用的沉浸式系统材质配置状态[MaterialState](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)，MaterialState中的[DEFAULT](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)、[ENABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)和[DISABLE](../reference/apis-arkui/arkts-apis-uimaterial.md#materialstate)，分别对应module.json5配置文件中default、enable和disable三个value值。

> **说明：**
>
> - 应用级开关设置为disable时，会全局禁用沉浸光感，默认开启或组件级开启的设置均不生效。
> - 组件级开启的优先级高于应用级开启的enable和default模式，开发者通过组件的沉浸式系统材质接口可以直接覆盖应用级开关开启的组件效果，反之不会。

## 关闭沉浸光感

关闭沉浸光感有以下几种方式：

1. 组件级关闭：组件级设置[uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty)。默认开启、应用级接入和组件级接入三种接入方式均可通过该操作关闭。

2. 应用级关闭：应用级开关设置为disable，只针对应用级开启的组件。

此外，部分组件的沉浸式系统材质由多个独立接口控制。以Select为例，其下拉按钮的沉浸式系统材质通过[systemMaterial](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)设置，下拉菜单的沉浸式系统材质通过独立的[menuSystemMaterial](../reference/apis-arkui/arkui-ts/ts-basic-components-select.md#menusystemmaterial)接口设置，两者相互独立、可分别开启或关闭。

> **说明：**
>
> [uiMaterial.Material.empty](../reference/apis-arkui/arkts-apis-uimaterial.md#empty)与将systemMaterial属性设置为undefined含义不同：undefined表示恢复为组件默认的沉浸光感接口效果；uiMaterial.Material.empty是关闭沉浸光感效果。因此，要关闭一个默认开启沉浸光感的组件，应使用uiMaterial.Material.empty。