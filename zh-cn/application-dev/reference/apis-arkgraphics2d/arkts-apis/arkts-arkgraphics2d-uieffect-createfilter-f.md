# createFilter

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createFilter

```TypeScript
function createFilter(): Filter
```

创建Filter实例用于给组件添加多种filter效果。

**起始版本：** 12

<!--Device-uiEffect-function createFilter(): Filter--><!--Device-uiEffect-function createFilter(): Filter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Filter](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-filter-i.md) | 返回Filter的头节点。 |

**示例：**

```TypeScript
// 创建Filter实例
let filter : uiEffect.Filter = uiEffect.createFilter();

```

