# DistortionParam（系统接口）

空间扭曲形变参数。

> **说明：**
>
> - 四个角的坐标可以按照如下坐标系设置。一个组件，左上角位置为[0, 0]，右上角位置为[1, 0]，左下角位置为[0, 1]，右下角位置为[1, 1]。
>
> - 如bottomLeft属性设置为[0.5, 0.5]，则表示左下角形变到组件中心点的位置，产生对应的形变效果。
>
> - 设置四个角坐标位置时请符合空间感逻辑。如topLeft = [0, 0.7]，bottomLeft = [0, 0.2]，左上角的位置低于左下角的位置，违背空间感的逻辑，可能导致渲染异常。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## barrelDistortion

```TypeScript
barrelDistortion: Vector4
```

四条边的桶形扭曲程度参数。

Vector4中四个值分别控制：x是左边，y是右边，z是上边，w是下边。

默认值：[0, 0, 0, 0]

正数表示边向外凸出的扭曲，负数表示边向内凹陷的扭曲。扭曲参数绝对值达到1时，扭曲程度为极端扭曲。

x、y、z、w 各值建议设置范围：[-1, 1]

**类型：** Vector4

**默认值：** [0, 0, 0, 0]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bottomLeft

```TypeScript
bottomLeft: Vector2
```

左下角的坐标。

默认值：[0, 1]

**类型：** Vector2

**默认值：** [0, 0]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## bottomRight

```TypeScript
bottomRight: Vector2
```

右下角的坐标。

默认值：[1, 1]

**类型：** Vector2

**默认值：** [0, 0]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## topLeft

```TypeScript
topLeft: Vector2
```

左上角的坐标。

默认值：[0, 0]

**类型：** Vector2

**默认值：** [0, 0]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## topRight

```TypeScript
topRight: Vector2
```

右上角的坐标。

默认值：[1, 0]

**类型：** Vector2

**默认值：** [0, 0]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

