# @ohos.arkui.uiMaterial(系统材质)

本模块提供系统材质的接口定义。不同的系统材质对应不同的UI效果，包括背景色backgroundColor、边框颜色borderColor、边框宽度borderWidth、阴影shadow、材质层滤镜[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter)效果。当前提供的系统材质为沉浸式材质类型[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)，沉浸式材质对象在不同设备上的表现存在差异，只有支持沉浸式材质的设备上设置才有效果，在不支持沉浸式材质的设备上可设置但无效果，可通过[uiMaterial.isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md)判断设备是否支持沉浸式材质。在支持沉浸式材质的设备上，材质效果在不同算力的设备上有分档表现，可通过[uiMaterial.getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md)获取设备的材质等级，分档效果具体参考[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)的描述。

开发指导请参考[沉浸光感](../../../ui/arkts-immersive-light-sense.md)指南文档。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) | 获取全局材质等级，与设备算力相关。在需要根据设备算力等级选择不同材质效果实现方式时，可调用此方法获取材质等级。该配置项由设备定义，不可修改。 |
| [getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md) | 获取当前应用的材质配置信息。在需要根据材质使能状态决定组件是否开启或关闭沉浸式系统材质效果时，可调用此方法获取配置信息。返回的配置信息来自应用在[module.json5](../../../quick-start/module-configuration-file.md)中配置的metadata。只有在entry类型的module中配置的metadata才会生效。 |
| [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) | 判断当前设备是否支持沉浸式系统材质[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)。在开发需要沉浸式材质效果的功能时，可先调用此方法判断设备是否支持，以决定是否为组件设置沉浸式材质。该配置项由设备定义，不可修改。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md) | 将一个[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)材质转换为适用于EffectComponent的ImmersiveMaterial材质。与convertToECSubMaterial的区别：本方法转换后的材质适用于EffectComponent本身，且materialColor、applyShadow、interactive、lightEffect属性不会生效；convertToECSubMaterial转换后的材质适用于EffectComponent的子组件。两者通常配合使用，以实现材质效果绘制的合并优化。 |
| [convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md) | 将一个[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)材质转换为适用于EffectComponent子组件的ImmersiveMaterial材质。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 沉浸式材质类，继承自[Material](arkts-arkui-uimaterial-material-c.md)。 |
| [Material](arkts-arkui-uimaterial-material-c.md) | 系统材质对象基类。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Material](arkts-arkui-uimaterial-material-c-sys.md) | 系统材质对象基类。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | 沉浸式材质参数。 |
| [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) | 沉浸式材质的光感交互反馈配置。光感交互反馈是指组件在用户触摸交互时，材质表面呈现动态光感变化的视觉效果。用于自定义反馈光感的颜色。 |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | 材质配置信息，包含材质使能状态和材质类型。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | 系统材质选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md) | 沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。开发者可根据UI场景需要选择合适的材质样式：悬浮按钮和轻量提示建议使用`ULTRA_THIN`或`THIN`样式，常规内容区域和卡片建议使用`REGULAR`样式，需要强调层次感或遮挡背景的场景建议使用`THICK`或`ULTRA_THICK`样式。 |
| [MaterialLevel](arkts-arkui-uimaterial-materiallevel-e.md) | 材质等级枚举，表示设备的算力等级。可通过[uiMaterial.getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md)获取当前设备的材质等级。 |
| [MaterialState](arkts-arkui-uimaterial-materialstate-e.md) | 材质使能状态枚举，表示应用级沉浸式系统材质配置的状态。 |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e.md) | 系统材质类型枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e-sys.md) | 沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。开发者可根据UI场景需要选择合适的材质样式：悬浮按钮和轻量提示建议使用`ULTRA_THIN`或`THIN`样式，常规内容区域和卡片建议使用`REGULAR`样式，需要强调层次感或遮挡背景的场景建议使用`THICK`或`ULTRA_THICK`样式。 |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e-sys.md) | 系统材质类型枚举。 |
<!--DelEnd-->

## 示例

```TypeScript
### 示例1（设置系统材质）

本示例介绍如何将半透明材质的Material对象通过[systemMaterial](../arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)属性设置给组件。


```

```TypeScript
### 示例2（使用EffectComponent设置系统材质）

本示例介绍如何将[uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)设置到[EffectComponent](../arkui-ts/ts-container-effectcomponent-sys.md)及其子组件上，包括直接使用EC样式材质，以及通过[uiMaterial.convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md)、[uiMaterial.convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md)将材质经过转换后设置两种方式。

从API版本26.0.0开始，新增uiMaterial.convertToECMaterial、uiMaterial.convertToECSubMaterial接口。
```

```TypeScript
### 示例1（设置沉浸式系统材质）

本示例介绍如何将沉浸式材质的[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)对象通过[systemMaterial](../arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial)属性设置给组件。

从API版本26.0.0开始，新增ImmersiveMaterial对象和systemMaterial属性。

在支持沉浸式材质的低算力设备上表现：

ULTRA_THIN样式：



THIN样式：



REGULAR样式：



THICK样式：



ULTRA_THICK样式：



在支持沉浸式材质的中算力设备上表现：

ULTRA_THIN样式：



THIN样式：



REGULAR样式：



THICK样式：



ULTRA_THICK样式：



在支持沉浸式材质的高算力设备上表现：

ULTRA_THIN样式：



THIN样式：



REGULAR样式：



THICK样式：



ULTRA_THICK样式：


```

```TypeScript
### 示例2（获取材质配置信息并使用空材质关闭沉浸式系统材质）

本示例介绍如何通过[uiMaterial.getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md)获取当前应用的材质配置信息，并根据配置状态使用empty关闭特定组件的沉浸式系统材质效果。

从API版本26.0.0开始，新增uiMaterial.getMaterialInfo方法和empty方法。

首先在[module.json5](../../../quick-start/module-configuration-file.md)文件中配置开关信息，需注意只有在entry类型的module中配置才会生效。
```

```TypeScript
然后按照如下内容编写示例代码。

在支持沉浸式材质的高算力设备上表现：



在支持沉浸式材质的中算力设备上表现：



在支持沉浸式材质的低算力设备上表现：


```

```TypeScript
### 示例3（设置组件材质的交互形变效果）

本示例介绍如何通过[ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md)中的interactive接口使组件实现交互形变效果。

从API版本26.0.0开始，新增interactive接口。

在支持沉浸式材质的高算力设备上表现：



在支持沉浸式材质的中算力设备上表现：



在支持沉浸式材质的低算力设备上表现：


```

```TypeScript
### 示例4（设置组件材质的光感交互反馈效果）

本示例介绍如何通过[ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md)中的lightEffect接口使组件实现光感交互反馈效果。

从API版本26.0.0开始，新增lightEffect接口。

在支持沉浸式材质的高算力设备上表现：



在支持沉浸式材质的中算力设备上表现：



在支持沉浸式材质的低算力设备上表现：


```

```TypeScript
### 示例5（查询材质等级与是否支持沉浸式材质）

本示例介绍如何通过[uiMaterial.getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md)获取设备的材质等级，并通过[uiMaterial.isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md)判断设备是否支持沉浸式材质，据此决定是否为组件设置沉浸式材质。通过此种适配方式，应用可以在支持和不支持沉浸式材质的不同设备上复用同一套代码，在不支持沉浸式材质的设备上自动降级为普通样式，无需为不同设备编写不同代码。

从API版本26.0.0开始，新增getGlobalMaterialLevel和isImmersiveMaterialSupported方法。
```
