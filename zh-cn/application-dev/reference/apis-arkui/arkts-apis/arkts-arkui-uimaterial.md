# @ohos.arkui.uiMaterial

本模块提供系统材质的接口定义。不同的系统材质对应不同的UI效果，包括背景色[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](../arkts-components/arkts-arkui-common-commonmethod-c.md#shadow-1)效果。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace uiMaterial--><!--Device-unnamed-declare namespace uiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md#getmaterialinfo-1) | 获取当前应用的材质配置信息。返回的配置信息来自应用在[module.json5](../../../../quick-start/module-configuration-file.md)中配置的metadata。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 沉浸式材质类，继承自[Material](arkts-arkui-uimaterial-materialtype-e-sys.md)。沉浸式材质根据设备算力有分档表现，设备算力的高、中、低档由设备厂商决定，定义在系统配置文件中。在高档和中档算力设备上，影响材质层滤镜效果和阴影[shadow](CommonMethod#shadow(value: ShadowOptions \| ShadowStyle))效果。在低档算力设备上，影响背景色[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色[borderColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](CommonMethod#shadow(value: ShadowOptions \| ShadowStyle))效果。且同一材质的效果，会受到设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置下，材质的参数和效果存在差异。 |
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
| [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) | 沉浸式材质的光感交互反馈配置。用于自定义反馈光感的颜色。 |
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
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md) | 沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。 |
| [MaterialState](arkts-arkui-uimaterial-materialstate-e.md) | 材质使能状态枚举，表示应用级沉浸式系统材质配置的状态。 |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e.md) | 系统材质类型枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e-sys.md) | 系统材质类型枚举。 |
<!--DelEnd-->

