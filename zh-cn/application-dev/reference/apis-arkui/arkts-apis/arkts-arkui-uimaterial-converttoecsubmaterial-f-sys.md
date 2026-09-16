# convertToECSubMaterial（系统接口）

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## convertToECSubMaterial

```TypeScript
function convertToECSubMaterial(material: uiMaterial.ImmersiveMaterial) : uiMaterial.ImmersiveMaterial
```

将一个[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)材质转换为适用于EffectComponent子组件的ImmersiveMaterial材质。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| material | [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 是 | 经过转换后适用于EffectComponent子组件的沉浸式材质，该材质配合EffectComponent使用以实现材质效果绘制的合并优化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | 经过转换后适用于EffectComponent子组件的沉浸式材质。 |
