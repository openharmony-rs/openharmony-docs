# borderRadiuses

## borderRadiuses

```TypeScript
export function borderRadiuses(all: number): BorderRadiuses
```

用于生成边框圆角均设置为传入值的边框圆角对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| all | number | 是 | 边框圆角。 单位：vp 取值范围：[0, +∞) 负数按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BorderRadiuses](arkts-arkui-borderradiuses-t.md) | 边框圆角均设置为传入值的边框圆角对象。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController, borderRadiuses } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 150,
  height: 150
};
renderNode.backgroundColor = 0xff519db4;
renderNode.borderRadius = borderRadiuses(32);


class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }.margin(20)
  }
}
```
