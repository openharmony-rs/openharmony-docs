# create

## 导入模块

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
function create(): DisplaySync
```

创建DisplaySync对象，通过此对象设置UI自绘制内容帧率。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-displaysync-i.md) | 返回DisplaySync对象实例，用于设置帧率范围、注册帧回调函数以及控制回调的启动和停止。 |

**示例**

```TypeScript
// 创建DisplaySync对象
let backDisplaySync: displaySync.DisplaySync = displaySync.create();
```
