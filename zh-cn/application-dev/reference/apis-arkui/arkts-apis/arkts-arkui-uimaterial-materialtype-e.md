# MaterialType（系统接口）

```TypeScript
enum MaterialType
```

系统材质类型枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## IMMERSIVE

```TypeScript
IMMERSIVE = 2
```

沉浸式材质类型。仅用于[MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md#MaterialInfo)接口的type属性标识当前配置的材质类型，不映射到底层功能。实际材质效果通过
[ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md#ImmersiveMaterial)类实现。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

