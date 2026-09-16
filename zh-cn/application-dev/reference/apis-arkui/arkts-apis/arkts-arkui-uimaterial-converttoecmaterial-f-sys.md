# convertToECMaterial（系统接口）

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## convertToECMaterial

```TypeScript
function convertToECMaterial(material: uiMaterial.ImmersiveMaterial) : uiMaterial.ImmersiveMaterial
```

将一个[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)材质转换为适用于EffectComponent的ImmersiveMaterial材质。与convertToECSubMaterial的区别：本方法转换后的材质适用于EffectComponent本身，且materialColor、applyShadow、interactive、lightEffect属性不会生效；convertToECSubMaterial转换后的材质适用于EffectComponent的子组件。两者通常配合使用，以实现材质效果绘制的合并优化。

EffectComponent组件上不生效材质中的[materialColor](arkts-arkui-uimaterial-immersiveoptions-i.md)、[applyShadow](arkts-arkui-uimaterial-immersiveoptions-i.md)、[interactive](arkts-arkui-uimaterial-immersiveoptions-i.md)、[lightEffect](arkts-arkui-uimaterial-immersiveoptions-i.md)属性，经过该接口转换后的材质若配置了上述属性，也将不会生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 是 | 待转换的沉浸式材质。注意：转换后材质中的[materialColor](arkts-arkui-uimaterial-immersiveoptions-i.md)、[applyShadow](arkts-arkui-uimaterial-immersiveoptions-i.md)、[interactive](arkts-arkui-uimaterial-immersiveoptions-i.md)、[lightEffect](arkts-arkui-uimaterial-immersiveoptions-i.md)属性将不会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 经过转换后适用于EffectComponent的沉浸式材质。转换后的材质不生效[materialColor](arkts-arkui-uimaterial-immersiveoptions-i.md)、[applyShadow](arkts-arkui-uimaterial-immersiveoptions-i.md)、[interactive](arkts-arkui-uimaterial-immersiveoptions-i.md)、[lightEffect](arkts-arkui-uimaterial-immersiveoptions-i.md)属性。 |
