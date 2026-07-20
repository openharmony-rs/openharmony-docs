# Material（系统接口）

系统材质对象基类。

**起始版本：** 26.0.0

<!--Device-uiMaterial-class Material--><!--Device-uiMaterial-class Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

<a id="empty"></a>
## empty

```TypeScript
static get empty(): Material
```

返回空材质对象，用于组件单独关闭沉浸式系统材质效果。使用方式为`uiMaterial.Material.empty`。

在enable模式下，可通过设置`systemMaterial(uiMaterial.Material.empty)`来单独关闭某个组件的沉浸式系统材质效果。如果组件未支持组件级沉浸式系统材质接口，则无法通过此方法关闭材质效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Material-static get empty(): Material--><!--Device-Material-static get empty(): Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Material](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-material-i.md) | 返回空材质对象，表示无材质效果。 |

