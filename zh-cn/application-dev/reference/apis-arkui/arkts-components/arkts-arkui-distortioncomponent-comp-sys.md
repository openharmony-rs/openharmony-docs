# DistortionComponent (System API)

Defines DistortionComponent.

## DistortionComponent

```TypeScript
DistortionComponent(options?: DistortionComponentOptions)
```

创建提供空间扭曲形变视效的组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DistortionComponentOptions](arkts-arkui-distortioncomponentoptions-i-sys.md) | 否 | 空间扭曲形变选项，用于配置组件的空间形变效果。不设置该参数或该参数设置为undefined时组件正常渲染、不施加任何形变效果。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [DistortionComponentOptions](arkts-arkui-distortioncomponentoptions-i-sys.md) | 空间扭曲形变选项。 |
| [DistortionParam](arkts-arkui-distortionparam-i-sys.md) | 空间扭曲形变参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Vector2](arkts-arkui-vector2-t-sys.md) | 二维向量类型，包含x和y坐标，表示位置坐标关系。 |
| [Vector4](arkts-arkui-vector4-t-sys.md) | 四维向量类型，包含x、y、z、w，各数值表示桶形形变程度。 |
