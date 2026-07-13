# LightSource（系统接口）

一个组件支持添加1个光源。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## color

```TypeScript
color?: ResourceColor
```

光源颜色。

默认值：Color.White

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity: number
```

光源强度，建议取值范围0-1。当光源强度为0时，光源不发光。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## positionX

```TypeScript
positionX: Dimension
```

光源相对于当前组件的X坐标。

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## positionY

```TypeScript
positionY: Dimension
```

光源相对于当前组件的Y坐标。

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## positionZ

```TypeScript
positionZ: Dimension
```

光源高度。光源越高，照射范围越大。

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

