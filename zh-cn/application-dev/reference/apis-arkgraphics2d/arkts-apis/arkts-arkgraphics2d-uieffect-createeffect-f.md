# createEffect

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

<a id="createeffect"></a>
## createEffect

```TypeScript
function createEffect(): VisualEffect
```

创建VisualEffect实例用于给组件添加多种effect效果。

**起始版本：** 12

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-uiEffect-function createEffect(): VisualEffect--><!--Device-uiEffect-function createEffect(): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VisualEffect](../../apis-arkui/arkts-components/arkts-arkui-visualeffect-t.md) | 返回VisualEffect的头节点。 |

**示例：**

```TypeScript
// 创建VisualEffect实例
let visualEffect : uiEffect.VisualEffect = uiEffect.createEffect();

```

