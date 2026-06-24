# @ohos.arkui.uiMaterial

本模块提供系统材质的接口定义。不同的系统材质对应不同的UI效果，包括背景色
[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框颜色
[borderColor](arkts-arkui-commonmethod-c.md#borderColor-1)、边框宽度[borderWidth](arkts-arkui-commonmethod-c.md#borderWidth-1)、阴影
[shadow](arkts-arkui-commonmethod-c.md#shadow-1)效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md#getMaterialInfo-1) | 获取当前应用的材质配置信息。返回的配置信息来自应用在[module.json5](../../../../quick-start/module-configuration-file.md)中配置的metadata。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 沉浸式材质类，继承自[Material](arkts-arkui-uimaterial-materialtype-e.md#MaterialType)。<br/><br/>沉浸式材质根据设备算力有分档表现，设备算力的高、中、低档由设备厂商决定，定义在系统配置文件中。在高档和中档算力设备上，影响材质层滤镜效果和阴影<br/>[shadow](CommonMethod#shadow(value: ShadowOptions \| ShadowStyle))效果。在低档算力设备上，影响背景色<br/>[backgroundColor](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、边框<br/>颜色[borderColor](arkts-arkui-commonmethod-c.md#borderColor-1)、边框宽度[borderWidth](arkts-arkui-commonmethod-c.md#borderWidth-1)、阴影<br/>[shadow](CommonMethod#shadow(value: ShadowOptions \| ShadowStyle))效果。且同一材质的效果，会受到设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置<br/>下，材质的参数和效果存在差异。<br/> |
| [Material](arkts-arkui-uimaterial-material-c.md) | 系统材质对象基类。<br/> |
| <!--DelRow-->[Material](arkts-arkui-uimaterial-material-c-sys.md) | 系统材质对象基类。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | 沉浸式材质参数。<br/> |
| [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) | 沉浸式材质的光感交互反馈配置。用于自定义反馈光感的颜色。<br/> |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | 材质配置信息，包含材质使能状态和材质类型。<br/> |
| <!--DelRow-->[MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | 系统材质选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md) | 沉浸式材质样式枚举。不同的材质样式对应不同的材质参数，主要包括材质的模糊程度、高光效果等。<br/> |
| [MaterialState](arkts-arkui-uimaterial-materialstate-e.md) | 材质使能状态枚举，表示应用级沉浸式系统材质配置的状态。<br/> |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e.md) | 系统材质类型枚举。<br/> |
| <!--DelRow-->[MaterialType](arkts-arkui-uimaterial-materialtype-e-sys.md) | 系统材质类型枚举。<br/> |

