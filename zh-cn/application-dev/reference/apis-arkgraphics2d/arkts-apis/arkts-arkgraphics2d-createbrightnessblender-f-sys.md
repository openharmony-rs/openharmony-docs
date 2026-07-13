# createBrightnessBlender（系统接口）

## createBrightnessBlender

```TypeScript
function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender
```

创建BrightnessBlender实例用于给组件添加提亮效果。

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | BrightnessBlenderParam | 是 | 实现提亮效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BrightnessBlender | 返回设置了提亮效果参数的BrightnessBlender。 |

**示例：**

```TypeScript
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})

```

