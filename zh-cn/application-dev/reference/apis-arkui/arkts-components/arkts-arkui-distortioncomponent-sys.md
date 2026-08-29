# DistortionComponent (System API)

Defines DistortionComponent.

## DistortionComponent

```TypeScript
DistortionComponent(options?: DistortionComponentOptions)
```

Creates a DistortionComponent with content.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DistortionComponentOptions | 否 | DistortionComponent Options. |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| DistortionComponentOptions | 空间扭曲形变选项。 |
| DistortionParam | 空间扭曲形变参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| Vector2 | 二维向量类型，包含x和y坐标，表示位置坐标关系。 |
| Vector4 | 四维向量类型，包含x、y、z、w，各数值表示桶形形变程度。 |
