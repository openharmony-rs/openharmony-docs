# ImmersiveMaterial

沉浸式材质类，继承自[Material](arkts-arkui-uimaterial-material-c.md)。

沉浸式材质根据设备是否支持沉浸式材质和设备算力有分档表现，可通过[uiMaterial.isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md)判断设备是否支持沉浸式材质，通过[uiMaterial.getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md)获取设备的材质等级。在不支持沉浸式材质的设备上可设置沉浸式材质但无效果。在支持沉浸式材质的高算力和中算力设备上，通过材质层滤镜属性[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter)和阴影shadow属性实现材质效果，当systemMaterial属性生效后，已设置的背景色属性backgroundColor会被恢复为透明色，已设置的边框宽度borderWidth属性会被恢复为无边框效果。在支持沉浸式材质的低算力设备上，通过背景色backgroundColor、边框颜色borderColor、边框宽度borderWidth、阴影shadow属性实现材质效果。同一材质的效果，会受到系统设置应用中沉浸光感配置项的影响，不同强弱程度的沉浸光感配置下，材质的参数和效果存在差异。

**继承/实现关系：** ImmersiveMaterial extends [Material](arkts-arkui-uimaterial-material-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ImmersiveOptions)
```

ImmersiveMaterial的构造函数。创建沉浸式材质对象，仅在支持沉浸式材质的设备上有效果，在不支持沉浸式材质的设备上可设置但无效果，可通过[uiMaterial.isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md)判断设备是否支持沉浸式材质。在支持沉浸式材质的设备上，根据设备算力等级有分档表现，可通过[uiMaterial.getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md)获取设备的材质等级。创建的ImmersiveMaterial对象需通过组件的systemMaterial通用属性设置到组件上才能生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | 否 | 系统材质配置选项，包括材质样式、材质层赋色等。<br>默认值参考ImmersiveOptions接口各参数的默认值，即`{style:uiMaterial.ImmersiveStyle.REGULAR, materialColor:undefined, colorInvert:false, applyShadow:true, interactive:false, lightEffect:undefined}`。 |
