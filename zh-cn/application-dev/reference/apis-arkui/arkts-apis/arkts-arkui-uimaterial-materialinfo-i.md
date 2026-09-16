# MaterialInfo

材质配置信息，包含材质使能状态和材质类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## state

```TypeScript
state: MaterialState
```

材质使能状态配置，决定当前应用沉浸式系统材质的使能模式。不同状态影响组件默认是否开启沉浸式系统材质效果，具体参考[MaterialState](arkts-arkui-uimaterial-materialstate-e.md)枚举说明。

**类型：** [MaterialState](arkts-arkui-uimaterial-materialstate-e.md)

**默认值：** MaterialState.DEFAULT

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: MaterialType
```

系统材质类型标识，表示当前配置对应的材质类型。该值仅用于类型标识，不映射到底层功能。

**类型：** [MaterialType](arkts-arkui-uimaterial-materialtype-e.md)

**默认值：** MaterialType.IMMERSIVE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
