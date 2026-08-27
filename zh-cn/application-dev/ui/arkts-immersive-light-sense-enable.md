# 开启沉浸光感
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

 沉浸光感提供默认开启、应用级开启和组件级开启三种方式，可按需选择。沉浸式系统材质由材质滤镜、折射、高光、阴影等多层效果叠加而成，需要大量GPU资源，具体的使用指导请参考沉浸光感功耗优化，其余开启后的常见问题请参考沉浸光感常见问题。

## 三种开启方式
> **说明：**
>
> 1. 开启后，不同组件的效果详见组件适配沉浸光感。
> 2. 开启沉浸光感，要确保应用的targetAPIVersion不低于26.0.0。如果低版本适配，适配指导请参考沉浸光感兼容性适配。
 不同开启方式支持的组件范围如下：

| 开启方式 | 支持的组件 | 说明 |
| --- | --- | --- |
| 默认开启 | 弹出框（Dialog）、AlphabetIndexer、SelectionMenu、即时反馈（Toast） | 应用从API版本26.0.0之前升级至API版本26.0.0及以上，在未主动设置沉浸光感的情况下，组件默认开启沉浸光感，无需任何配置。|
| 应用级开启 | 组件清单详见MaterialState。 | 通过module.json5统一配置，为支持沉浸光感的组件，批量开启或全局禁用沉浸光感，具体开启方法请参考应用级开启。|
| 组件级开启 | 支持设置沉浸式系统材质的组件 | 支持通过如下三种方式开启：<br/> 1. 通过通用属性systemMaterial设置。<br/>2. 弹窗类组件通过options参数中的systemMaterial字段设置。<br/>3. 组件专属接口设置，当前支持设置的组件包括：Select下拉菜单的menuSystemMaterial、Navigation标题栏的systemMaterial字段。 |

### 应用级开启

在module.json5中，配置metadata参数的name字段配置为"ohos.arkui.UIMaterial.state"，value字段可以为default、enable和disable。该配置仅在entry类型的module中生效。

以下示例展示如何在module.json5中配置enable模式：

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

开发者可以通过uiMaterial.getMaterialInfo()获取当前应用的沉浸式系统材质配置状态MaterialState，MaterialState中的DEFAULT、ENABLE和DISABLE，分别对应module.json5配置文件中default、enable和disable三个value值。

> **说明：**
>
> - 应用级开关设置为disable时，会全局禁用沉浸光感，默认开启或组件级开启的设置均不生效。
> - 组件级开启的优先级高于应用级开启的enable和default模式，开发者通过组件的沉浸式系统材质接口可以直接覆盖应用级开关开启的组件效果，反之不会。

## 关闭沉浸光感

关闭沉浸光感效果有以下几种方式：

1. 组件级关闭：组件级设置uiMaterial.Material.empty。默认开启、应用级接入和组件级接入三种接入方式均可通过该操作关闭。

2. 应用级关闭：应用级开关设置为disable，只针对应用级开启的组件。

此外，部分组件的沉浸式系统材质由多个独立接口控制。以Select为例，其下拉按钮的沉浸式系统材质通过systemMaterial设置，下拉菜单的沉浸式系统材质通过独立的menuSystemMaterial接口设置，两者相互独立、可分别开启或关闭。

> **说明：**
>
> uiMaterial.Material.empty与将systemMaterial属性设置为undefined含义不同：undefined表示恢复为组件默认的沉浸光感接口效果；uiMaterial.Material.empty是关闭沉浸光感效果。因此，要关闭一个默认开启沉浸光感的组件，应使用uiMaterial.Material.empty。