# MaterialInfo

材质配置信息，包含材质使能状态和材质类型。

**起始版本：** 26.0.0

<!--Device-uiMaterial-interface MaterialInfo--><!--Device-uiMaterial-interface MaterialInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## state

```TypeScript
state: MaterialState
```

材质使能状态配置。

**类型：** MaterialState

**默认值：** MaterialState.DEFAULT

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MaterialInfo-state: MaterialState--><!--Device-MaterialInfo-state: MaterialState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: MaterialType
```

材质类型标识，表示当前配置对应的材质类型。该值仅用于类型标识，不映射到底层功能。

**类型：** MaterialType

**默认值：** MaterialType.IMMERSIVE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MaterialInfo-type: MaterialType--><!--Device-MaterialInfo-type: MaterialType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

