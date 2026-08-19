# RenderNode

提供自绘制渲染节点RenderNode，支持开发者通过C API进行开发，完成自定义绘制需求。RenderNode还支持渲染节点树管理（添加、删除、查询子节点）、背景色与不透明度等视觉属性设置、变换（缩放、旋转、平移、变换矩阵）、阴影 、边框、遮罩与裁剪、模糊效果等能力，适用于在Stage模型下进行自定义渲染与节点树管理的场景。 > **说明：** > > - 不建议对BuilderNode中的RenderNode进行修改操作。BuilderNode中持有的FrameNode仅用于将该 > BuilderNode作为子节点挂载到其他FrameNode上，对该FrameNode或对应的RenderNode进行属性设置与子节点操作可能会产生未定义行为，包括但不限于显示异常、事件异常、稳定性问题等。 > > - RenderNode对象不支持使用JSON序列化。

**起始版本：** 11

<!--Device-unnamed-export class RenderNode--><!--Device-unnamed-export class RenderNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## appendChild

```TypeScript
appendChild(node: RenderNode): void
```

在RenderNode最后一个子节点后添加新的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-appendChild(node: RenderNode): void--><!--Device-RenderNode-appendChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 是 | 需要添加的RenderNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: its corresponding FrameNode cannot be adopted."<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 100,
  height: 100
};
renderNode.backgroundColor = 0xffff0000;
const child = new RenderNode();
child.frame = {
  x: 10,
  y: 10,
  width: 50,
  height: 50
};
child.backgroundColor = 0xff00ff00;
renderNode.appendChild(child);

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      // 在RenderNode最后一个子节点后添加新的子节点
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
    }
  }
}
```

## clearChildren

```TypeScript
clearChildren(): void
```

清除当前RenderNode的所有子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-clearChildren(): void--><!--Device-RenderNode-clearChildren(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.size = { width: 200, height: 300 };
for (let i = 0; i < 10; i++) {
  let childNode = new RenderNode();
  childNode.size = { width: i * 10, height: i * 10 };
  childNode.position = { x: i * 10, y: i * 10 };
  childNode.backgroundColor = 0xFF0000FF - 0X11 * i;
  renderNode.appendChild(childNode);
}

// 继承NodeController实现自定义UI控制器
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
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(200)
        .height(300)
      Button('clearChildren')
        .onClick(() => {
          renderNode.clearChildren(); // 清除renderNode的所有子节点
        })
    }.width('100%')
  }
}
```

## constructor

```TypeScript
constructor()
```

RenderNode的构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-constructor()--><!--Device-RenderNode-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 100,
  height: 100
};
renderNode.backgroundColor = 0xffff0000;

// 继承NodeController实现自定义UI控制器
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
    }
  }
}
```

## dispose

```TypeScript
dispose(): void
```

立即释放当前RenderNode。调用此方法后，RenderNode将解除与后端实体节点的引用关系，再次调用该节点的接口可能会出现crash或返回默认值。可通过 [isDisposed](../../apis-na/arkts-apis/arkts-na-rendernode-c.md#isdisposed)接口查询节点是否已释放。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-dispose(): void--><!--Device-RenderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = { x: 0, y: 100, width: 100, height: 100 };
renderNode.backgroundColor = 0xffff0000;

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 200, height: 200 };
      rootRenderNode.backgroundColor = 0xff00ff00;
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }

  disposeRenderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    // 释放当前renderNode前，从父节点rootRenderNode中移除该renderNode
    if (rootRenderNode !== null) {
      rootRenderNode.removeChild(renderNode);
    }
    renderNode.dispose();
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('RenderNode dispose')
        .onClick(() => {
          this.myNodeController.disposeRenderNode();
        })
        .width('100%')
    }
  }
}
```

## draw

```TypeScript
draw(context: DrawContext): void
```

绘制方法，需要开发者进行实现。该方法会在RenderNode进行绘制时被调用。 该接口的[DrawContext](arkts-arkui-graphics-drawcontext-c.md)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见 [调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-arktsNode-renderNode.md#调整自定义绘制canvas的变换矩阵)。 > **说明：** > > RenderNode初始化时，会调用两次draw方法。第一次调用是在首次创建FrameNode时触发Render流程，第二次调用是在首次设置modifier时触发绘制。后续绘制流程皆由modifier触发。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-draw(context: DrawContext): void--><!--Device-RenderNode-draw(context: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | 是 | 图形绘制上下文。 |

**示例**

ArkTS侧代码：

```TypeScript
// Index.ets
import bridge from 'libentry.so'; // 该 .so 文件由开发者通过 NAPI 编写并生成
import { RenderNode, FrameNode, NodeController, DrawContext } from '@kit.ArkUI';

// 继承RenderNode，实现自定义绘制方法
class MyRenderNode extends RenderNode {
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  // 绘制RenderNode时调用此函数
  draw(context: DrawContext) {
    // 需要将 context 中的宽度和高度从vp转换为px
    bridge.nativeOnDraw(0, context, this.uiContext.vp2px(context.size.width), this.uiContext.vp2px(context.size.height));
  }
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      const renderNode = new MyRenderNode(uiContext);
      renderNode.size = { width: 100, height: 100 };
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
    }
  }
}
```

C++侧可通过NAPI来获取Canvas，并进行后续的自定义绘制操作。

```TypeScript
// native_bridge.cpp
#include "napi/native_api.h"
#include <native_drawing/drawing_canvas.h>
#include <native_drawing/drawing_color.h>
#include <native_drawing/drawing_path.h>
#include <native_drawing/drawing_pen.h>

static napi_value OnDraw(napi_env env, napi_callback_info info)
{
    size_t argc = 4;
    napi_value args[4] = { nullptr };
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int32_t id;
    napi_get_value_int32(env, args[0], &id);
    
    // 获取 Canvas 指针
    void* temp = nullptr;
    napi_unwrap(env, args[1], &temp);
    OH_Drawing_Canvas *canvas = reinterpret_cast<OH_Drawing_Canvas*>(temp);
    
    // 获取 Canvas 宽度
    int32_t width;
    napi_get_value_int32(env, args[2], &width);
    
    // 获取 Canvas 高度
    int32_t height;
    napi_get_value_int32(env, args[3], &height);
    
    // 传入canvas、height、width等信息至绘制函数中进行自定义绘制
    auto path = OH_Drawing_PathCreate();
    OH_Drawing_PathMoveTo(path, width / 4, height / 4);
    OH_Drawing_PathLineTo(path, width * 3 / 4, height / 4);
    OH_Drawing_PathLineTo(path, width * 3 / 4, height * 3 / 4);
    OH_Drawing_PathLineTo(path, width / 4, height * 3 / 4);
    OH_Drawing_PathLineTo(path, width / 4, height / 4);
    OH_Drawing_PathClose(path);
    
    auto pen = OH_Drawing_PenCreate();
    OH_Drawing_PenSetWidth(pen, 10);
    OH_Drawing_PenSetColor(pen, OH_Drawing_ColorSetArgb(0xFF, 0xFF, 0x00, 0x00));
    OH_Drawing_CanvasAttachPen(canvas, pen);
    
    OH_Drawing_CanvasDrawPath(canvas, path);
    OH_Drawing_CanvasDetachPen(canvas);
    OH_Drawing_PenDestroy(pen);
    OH_Drawing_PathDestroy(path);

    return nullptr;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = {
        { "nativeOnDraw", nullptr, OnDraw, nullptr, nullptr, nullptr, napi_default, nullptr }
    };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END

static napi_module demoModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = ((void*)0),
    .reserved = { 0 },
};

extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
{
    napi_module_register(&demoModule);
}
```

修改工程中的文件，添加如下内容：

同时在工程中的文件中，添加自定义绘制函数在ArkTS侧的定义，如：

```TypeScript
import { DrawContext } from '@kit.ArkUI';

export const nativeOnDraw: (id: number, context: DrawContext, width: number, height: number) => number;
```

## getChild

```TypeScript
getChild(index: number): RenderNode | null
```

获取当前RenderNode指定位置的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getChild(index: number): RenderNode | null--><!--Device-RenderNode-getChild(index: number): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号，从0开始。取值范围：[0, 子节点数量-1]，超出范围时返回null。不支持负索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 子节点。若该RenderNode不包含所查询的子节点，则返回空对象null。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.size = { width: 200, height: 300 };
for (let i = 0; i < 10; i++) {
  let childNode = new RenderNode();
  childNode.size = { width: i * 10, height: i * 10 };
  childNode.position = { x: i * 10, y: i * 10 };
  childNode.backgroundColor = 0xFF0000FF - 0X11 * i;
  renderNode.appendChild(childNode);
}

// 继承NodeController实现自定义UI控制器
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
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(200)
        .height(300)
      Button('getChild')
        .onClick(() => {
          for (let i = 0; i < 11; i++) {
            let childNode: RenderNode | null = renderNode.getChild(i);
            if (childNode === null) {
              // renderNode不存在序列号为10的子节点，此时返回null
              console.error(`the ${i} of renderNode's childNode is null`);
            } else {
              // 正常获取子节点并打印节点属性
              console.info(`the ${i} of renderNode's childNode has a size of {${childNode.size.width},${childNode.size.height}}`);
            }
          }

        })
    }.width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
import {
  Entry,
  RenderNode,
  FrameNode,
  NodeController,
  UIContext,
  Component,
  Column,
  NodeContainer,
  Button
} from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.size = { width: 200, height: 300 };
for (let i = 0; i < 10; i++) {
  let childNode = new RenderNode();
  childNode.size = { width: i * 10, height: i * 10 };
  childNode.position = { x: i * 10, y: i * 10 };
  childNode.backgroundColor = 0xFF0000FF.toInt() - 0X11 * i;
  renderNode.appendChild(childNode);
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode!.getRenderNode();
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
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(200)
        .height(300)
      Button("getChild")
        .onClick(() => {
          for (let i = 0; i < 11; i++) {
            let childNode: RenderNode | null = renderNode.getChild(i);
            if (childNode == null) {
              console.info(`the ${i} of renderNode's childNode is null`);
            } else {
              console.info(`the ${i} of renderNode's childNode has a size of {${childNode.size.width},${childNode.size.height}}`);
            }
          }

        })
    }.width("100%")
  }
}
```

## getFirstChild

```TypeScript
getFirstChild(): RenderNode | null
```

获取当前RenderNode的第一个子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getFirstChild(): RenderNode | null--><!--Device-RenderNode-getFirstChild(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 首个子节点。若该RenderNode不包含子节点，则返回空对象null。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 200,
  height: 350
};
renderNode.backgroundColor = 0xffff0000;
for (let i = 0; i < 5; i++) {
  const node = new RenderNode();
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  node.backgroundColor = 0xff00ff00;
  renderNode.appendChild(node);
}

// 继承NodeController实现自定义UI控制器
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
        .width(200)
        .height(350)
      Button('getFirstChild')
        .onClick(() => {
          // 获取renderNode的首个子节点
          const firstChild = renderNode.getFirstChild();
          if (firstChild === null) {
            console.error(`the first child is null`);
          } else {
            console.info(`the position of first child is x: ${firstChild.position.x}, y: ${firstChild.position.y}`);
          }
        })
    }
  }
}
```

## getNextSibling

```TypeScript
getNextSibling(): RenderNode | null
```

获取当前RenderNode的下一个同级节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getNextSibling(): RenderNode | null--><!--Device-RenderNode-getNextSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 当前RenderNode的下一个同级节点。若该RenderNode不包含下一个同级节点，则返回空对象null。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 200,
  height: 350
};
renderNode.backgroundColor = 0xffff0000;
for (let i = 0; i < 5; i++) {
  const node = new RenderNode();
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  node.backgroundColor = 0xff00ff00;
  renderNode.appendChild(node);
}

// 继承NodeController实现自定义UI控制器
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
        .width(200)
        .height(350)
      Button('getNextSibling')
        .onClick(() => {
          const child = renderNode.getChild(1); 
          if (child === null) {
            console.error(`the child is null`);
          } else {
            // 获取renderNode序列号为1的子节点后，再获取它的下一个同级节点
            const nextSibling = child.getNextSibling();
            if (nextSibling === null) {
              console.error(`the nextSibling is null`);
            } else {
              console.info(`the position of child is x: ${child.position.x}, y: ${child.position.y}, the position of nextSibling is x: ${nextSibling.position.x}, y: ${nextSibling.position.y}`);
            }
          }
        })
    }
  }
}
```

## getPreviousSibling

```TypeScript
getPreviousSibling(): RenderNode | null
```

获取当前RenderNode的上一个同级节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-getPreviousSibling(): RenderNode | null--><!--Device-RenderNode-getPreviousSibling(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 当前RenderNode的上一个同级节点。若该RenderNode不包含上一个同级节点，则返回空对象null。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 200,
  height: 350
};
renderNode.backgroundColor = 0xffff0000;
for (let i = 0; i < 5; i++) {
  const node = new RenderNode();
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  node.backgroundColor = 0xff00ff00;
  renderNode.appendChild(node);
}

// 继承NodeController实现自定义UI控制器
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
        .width(200)
        .height(350)
      Button('getPreviousSibling')
        .onClick(() => {
          const child = renderNode.getChild(1);
          if (child === null) {
            console.error(`the child is null`);
          } else {
            // 获取renderNode序列号为1的子节点后，再获取它的上一个同级节点
            const previousSibling = child.getPreviousSibling();
            if (previousSibling === null) {
              console.error(`the previousSibling is null`);
            } else {
              console.info(`the position of child is x: ${child.position.x}, y: ${child.position.y}, the position of previousSibling is x: ${previousSibling.position.x}, y: ${previousSibling.position.y}`);
            }
          }
        })
    }
  }
}
```

## insertChildAfter

```TypeScript
insertChildAfter(child: RenderNode, sibling: RenderNode | null): void
```

在RenderNode指定子节点之后添加新的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void--><!--Device-RenderNode-insertChildAfter(child: RenderNode, sibling: RenderNode | null): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 是 | 需要添加的子节点。 |
| sibling | [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) \| null | 是 | 新节点将插入到该节点之后。若该参数设置为空，则新节点将插入到首个子节点之前。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: its corresponding FrameNode cannot be adopted."<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 200,
  height: 350
};
renderNode.backgroundColor = 0xffff0000;
for (let i = 0; i < 5; i++) {
  const node = new RenderNode();
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  node.backgroundColor = 0xff00ff00;
  renderNode.appendChild(node);
}

const child = new RenderNode();
child.frame = {
  x: 70,
  y: 70,
  width: 50,
  height: 50
};
child.backgroundColor = 0xffffff00;
const sibling = renderNode.getChild(1);
// 将child节点插入至sibling节点之后
renderNode.insertChildAfter(child, sibling);

// 继承NodeController实现自定义UI控制器
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
    }
  }
}
```

## invalidate

```TypeScript
invalidate(): void
```

该方法会触发RenderNode的重新渲染，重新渲染时会调用[draw](../../apis-na/arkts-apis/arkts-na-rendernode-c.md#draw)方法。若开发者继承了RenderNode并实现了draw方法，调用invalidate()后将重新执行draw方 法中的绘制逻辑。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-invalidate(): void--><!--Device-RenderNode-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import bridge from 'libentry.so'; // 该 .so 文件由开发者通过 NAPI 编写并生成
import { RenderNode, FrameNode, NodeController, DrawContext } from '@kit.ArkUI';

// 继承RenderNode，实现自定义绘制方法
class MyRenderNode extends RenderNode {
  uiContext: UIContext;

  constructor(uiContext: UIContext) {
    super();
    this.uiContext = uiContext;
  }

  draw(context: DrawContext) {
    // 需要将 context 中的宽度和高度从vp转换为px
    bridge.nativeOnDraw(0, context, this.uiContext.vp2px(context.size.width), this.uiContext.vp2px(context.size.height));
  }
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  newNode: MyRenderNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    const renderNode = this.rootNode.getRenderNode();
    if (renderNode === null) {
      return this.rootNode;
    }
    this.newNode = new MyRenderNode(uiContext);
    this.newNode.size = { width: 100, height: 100 };
    renderNode.appendChild(this.newNode);
    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      Column() {
        NodeContainer(this.myNodeController)
          .width('100%')
        Button('Invalidate')
          .onClick(() => {
            // 触发RenderNode的重新渲染
            this.myNodeController.newNode?.invalidate();
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前RenderNode对象是否已解除与后端实体节点的引用关系。当节点调用dispose接口后，再次调用其他接口可能会出现crash、返回默认值的情况，建议开发者在操作节点前调用此接口检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-isDisposed(): boolean--><!--Device-RenderNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true表示节点已与后端实体节点解除引用，false表示节点未与后端实体节点解除引用。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = { x: 100, y: 100, width: 100, height: 100 };
renderNode.backgroundColor = 0xff2787d9;

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 300, height: 300 };
      rootRenderNode.backgroundColor = 0xffd5d5d5;
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }

  disposeRenderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.removeChild(renderNode);
    }
    renderNode.dispose();
  }

  isDisposed() : string {
    if (renderNode !== null) {
      // 检查当前renderNode是否已经与后端节点解除引用
      if (renderNode.isDisposed()) {
        return 'renderNode isDisposed is true';
      } else {
        return 'renderNode isDisposed is false';
      }
    }
    return 'renderNode is null';
  }
}

@Entry
@Component
struct Index {
  @State text: string = ''
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('RenderNode dispose')
        .onClick(() => {
          this.myNodeController.disposeRenderNode();
          this.text = '';
        })
        .width(200)
        .height(50)
      Button('RenderNode isDisposed')
        .onClick(() => {
          this.text = this.myNodeController.isDisposed();
        })
        .width(200)
        .height(50)
      Text(this.text)
        .fontSize(25)
    }
    .width('100%')
    .height('100%')
  }
}
```

## removeChild

```TypeScript
removeChild(node: RenderNode): void
```

从RenderNode中删除指定的子节点。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RenderNode-removeChild(node: RenderNode): void--><!--Device-RenderNode-removeChild(node: RenderNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md) | 是 | 需要删除的子节点。 |

**示例**

```TypeScript
import { RenderNode, FrameNode, NodeController } from '@kit.ArkUI';

const renderNode = new RenderNode();
renderNode.frame = {
  x: 0,
  y: 0,
  width: 200,
  height: 350
};
renderNode.backgroundColor = 0xffff0000;
for (let i = 0; i < 5; i++) {
  const node = new RenderNode();
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  node.backgroundColor = 0xff00ff00;
  renderNode.appendChild(node);
}

// 删除renderNode下序列号为1的子节点
const node = renderNode.getChild(1);
renderNode.removeChild(node);

// 继承NodeController实现自定义UI控制器
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
    }
  }
}
```

