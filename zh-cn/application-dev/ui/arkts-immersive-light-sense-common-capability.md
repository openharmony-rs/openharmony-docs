# 定制沉浸式系统材质效果
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本文介绍如何按场景定制沉浸式系统材质效果，包括薄材质下保障文字可读、为沉浸式系统材质赋予色调、按压触摸时增强交互反馈以及为沉浸式系统材质使用自定义阴影。

## 保障文字可读

当组件设置为透明度较高的沉浸式系统材质（如ULTRA_THIN或THIN）时，组件内的文字可能与背景色对比度不足，导致阅读体验不佳。开启[ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)中的colorInvert自动反色功能后，组件子节点中的文字颜色会自动调整为沉浸式系统材质下方背景色的反色，确保文字始终可读。说明如下：

- 自动反色仅在高算力和中算力设备上生效，低算力设备上设置colorInvert不会产生视觉效果差异。
- 自动反色仅在沉浸式系统材质足够薄时生效，材质样式为THIN或ULTRA_THIN。
- 自动反色与系统沉浸光感的强弱配置相关，沉浸式系统材质越薄、沉浸光感越强，越容易符合反色要求。
- 自动反色仅对通过资源接口设置的颜色值生效，使用代码中硬编码的颜色值（如`Color.White`、`'#FFFFFFFF'`）不会触发自动反色。完整生效属性清单请参见[colorInvert](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数说明。

如开启自动反色后文字颜色没有变化，排查步骤请参见[开启自动反色后文字颜色没有变化](arkts-immersive-light-sense-faq.md#开启自动反色后文字颜色没有变化)。

## 为材质层赋色

通过[ImmersiveOptions](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)中的[materialColor](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数，可为材质滤镜再混合一层纯色效果，用于色调表达或降低折射的可见程度。该颜色需要带有一定的透明度，传入纯不透明颜色（如`Color.Red`或`'#FFFF0000'`）会遮挡材质滤镜效果。

> **说明：**
>
> materialColor参数对所有档位的算力设备均生效。在高算力和中算力设备上，该参数为材质滤镜再混合一层纯色效果；在低算力设备上，该参数作为背景色[backgroundColor](../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)属性值。

## 增强交互反馈

- **交互形变**：通过[interactive](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数开启后，组件在按压时产生弹性形变，松手后自动恢复，增强交互的视觉反馈。
- **点光源**：通过[lightEffect](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)参数开启后，用户手指触摸组件时会产生流光跟随效果。lightEffect传入有效对象即启用，传入null或undefined则不启用；对象中的color字段自定义流光颜色，默认值为Color.White。

## 控制材质阴影

沉浸式系统材质默认自带阴影效果（[applyShadow](../reference/apis-arkui/arkts-apis-uimaterial.md#immersiveoptions)为true），优先于[shadow](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow)通用属性，此时自定义的shadow设置不会生效。如需使用自定义阴影，将applyShadow置为false后再设置shadow，沉浸式系统材质的阴影效果即不生效。
