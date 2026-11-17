# ImmersiveOptions（系统接口）

```TypeScript
interface ImmersiveOptions
```

沉浸式材质参数。

**起始版本：** 26.0.0

<!--Device-uiMaterial-interface ImmersiveOptions--><!--Device-uiMaterial-interface ImmersiveOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## colorBlendMode

```TypeScript
colorBlendMode?: MaterialColorBlendMode
```

材质颜色混色模式。默认值：uiMaterial.MaterialColorBlendMode.LINEAR_MIX。**说明：** 1. 该参数仅对支持沉浸式材质的高算力和中算力设备的显示效果生效。
2. **TINTED_GLASS**仅对部分组件生效，当前支持的组件包括：Button、Chip、ChipGroup、Toggle，其他组件设置无效。

**类型：** [MaterialColorBlendMode](arkts-arkui-uimaterial-materialcolorblendmode-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImmersiveOptions-colorBlendMode?: MaterialColorBlendMode--><!--Device-ImmersiveOptions-colorBlendMode?: MaterialColorBlendMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
