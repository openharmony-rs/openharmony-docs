# create

## 导入模块

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

<a id="create"></a>
## create

```TypeScript
function create(): DisplaySync
```

创建DisplaySync对象，通过此对象设置UI自绘制内容帧率。

**起始版本：** 11

<!--Device-displaySync-function create(): DisplaySync--><!--Device-displaySync-function create(): DisplaySync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-displaysync-i.md) | 返回当前创建的DisplaySync对象实例。 |

**示例：**

```TypeScript
// 创建DisplaySync对象
let backDisplaySync: displaySync.DisplaySync = displaySync.create();

```

