# 自定义渲染节点 (RenderNode)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

对于不具备自己的渲染环境的三方框架，尽管已实现前端解析、布局及事件处理等功能，但仍需依赖系统的基础渲染和动画能力。[FrameNode](./arkts-user-defined-arktsNode-frameNode.md)上的通用属性与通用事件对这类框架而言是冗余的，会导致多次不必要的操作，涵盖布局、事件处理等逻辑。

自定义渲染节点 ([RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md))是更加轻量的渲染节点，仅具备与渲染相关的功能。它提供了设置基础渲染属性的能力，以及节点的动态添加、删除和自定义绘制的能力。RenderNode能够为第三方框架提供基础的渲染和动画支持。

## 创建和删除节点

RenderNode提供了节点创建和删除的能力。可以通过RenderNode的构造函数创建自定义的RenderNode节点。通过构造函数创建的节点对应一个实体的节点。同时，可以通过RenderNode中的[dispose](../reference/apis-arkui/js-apis-arkui-renderNode.md#dispose12)接口来实现与实体节点的绑定关系的解除。

## 操作节点树

RenderNode提供了节点的增、删、查、改的能力，能够修改节点的子树结构；可以对所有RenderNode的节点的父子节点做出查询操作，并返回查询结果。

> **说明：**
>
> - RenderNode中查询获取得到的子树结构按照开发通过RenderNode的接口传递的参数构建。
>
> - RenderNode如果要与系统直接结合显示，使用需要依赖FrameNode中获取的RenderNode进行挂载上树。

<!-- @[operation_node_tree](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/OperationNodeTree.ets) -->

``` TypeScript
import { FrameNode, NodeController, RenderNode } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

const TEST_TAG: string = 'RenderNode';
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
  // 设置node节点的Frame大小
  node.frame = {
    x: 10,
    y: 10 + 60 * i,
    width: 50,
    height: 50
  };
  // 设置node节点的背景颜色
  node.backgroundColor = 0xff00ff00;
  // 将新增节点挂载在renderNode上
  renderNode.appendChild(node);
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode?.getRenderNode();
    if (rootRenderNode) {
      rootRenderNode.appendChild(renderNode);
    }
    return this.rootNode;
  }
}

@Entry
@Component
export struct OperationNodeTree {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    // ···
      Row() {
        NodeContainer(this.myNodeController)
          .width(200)
          .height(350);
        Button('getNextSibling')
          .onClick(() => {
            const child = renderNode.getChild(1);
            const nextSibling = child!.getNextSibling()
            if (child === null || nextSibling === null) {
              hilog.info(DOMAIN, TEST_TAG, ' the child or nextChild is null');
            } else {
              // 获取子节点的位置信息
              hilog.info(DOMAIN, TEST_TAG, `the position of child is x: ${child.position.x}, y: ${child.position.y}, ` +
                `the position of nextSibling is x: ${nextSibling.position.x}, y: ${nextSibling.position.y}`);
            }
          });
      };

    // ···
  }
}

```

## 设置和获取渲染相关属性

RenderNode中可以设置渲染相关的属性，包括：[backgroundColor](../reference/apis-arkui/js-apis-arkui-renderNode.md#backgroundcolor)，[clipToFrame](../reference/apis-arkui/js-apis-arkui-renderNode.md#cliptoframe)，[opacity](../reference/apis-arkui/js-apis-arkui-renderNode.md#opacity)，[size](../reference/apis-arkui/js-apis-arkui-renderNode.md#size)，[position](../reference/apis-arkui/js-apis-arkui-renderNode.md#position)，[frame](../reference/apis-arkui/js-apis-arkui-renderNode.md#frame)，[pivot](../reference/apis-arkui/js-apis-arkui-renderNode.md#pivot)，[scale](../reference/apis-arkui/js-apis-arkui-renderNode.md#scale)，[translation](../reference/apis-arkui/js-apis-arkui-renderNode.md#translation)，[rotation](../reference/apis-arkui/js-apis-arkui-renderNode.md#rotation)，[transform](../reference/apis-arkui/js-apis-arkui-renderNode.md#transform)，[shadowColor](../reference/apis-arkui/js-apis-arkui-renderNode.md#shadowcolor)，[shadowOffset](../reference/apis-arkui/js-apis-arkui-renderNode.md#shadowoffset)，[shadowAlpha](../reference/apis-arkui/js-apis-arkui-renderNode.md#shadowalpha)，[shadowElevation](../reference/apis-arkui/js-apis-arkui-renderNode.md#shadowelevation)，[shadowRadius](../reference/apis-arkui/js-apis-arkui-renderNode.md#shadowradius)，[borderStyle](../reference/apis-arkui/js-apis-arkui-renderNode.md#borderstyle12)，[borderWidth](../reference/apis-arkui/js-apis-arkui-renderNode.md#borderwidth12)，[borderColor](../reference/apis-arkui/js-apis-arkui-renderNode.md#bordercolor12)，[borderRadius](../reference/apis-arkui/js-apis-arkui-renderNode.md#borderradius12)，[shapeMask](../reference/apis-arkui/js-apis-arkui-renderNode.md#shapemask12)，[shapeClip](../reference/apis-arkui/js-apis-arkui-renderNode.md#shapeclip12)，[markNodeGroup](../reference/apis-arkui/js-apis-arkui-renderNode.md#marknodegroup12)等。具体属性支持范围参考[RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md)接口说明。

> **说明：**
> 
> - RenderNode中查询获取得到的属性为设置的属性值。
> 
> - 若未传入参数或者传入参数为非法值则查询获得的为默认值。
>
> - 不建议对BuilderNode中的RenderNode进行修改操作。BuilderNode中具体属性设置是由状态管理实现的，属性更新的时序开发者不可控，BuilderNode和FrameNode中同时设置RenderNode属性可能会导致RenderNode属性设置与预期不相符。

<!-- @[rendering_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/RenderingProperties.ets) -->

``` TypeScript
import { RenderNode, FrameNode, NodeController, ShapeMask, ShapeClip } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

const TEST_TAG: string = 'RenderNode';
const mask = new ShapeMask();
mask.setRectShape({
  left: 0,
  right: 150,
  top: 0,
  bottom: 150
});
mask.fillColor = 0X55FF0000;
mask.strokeColor = 0XFFFF0000;
mask.strokeWidth = 24;

const clip = new ShapeClip();
clip.setCommandPath({ commands: 'M100 0 L0 100 L50 200 L150 200 L200 100 Z' });

const renderNode = new RenderNode();
renderNode.backgroundColor = 0xffff0000;
renderNode.size = { width: 100, height: 100 };

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
export struct RenderingProperties {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    // ···
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceBetween }) {
        Column() {
          NodeContainer(this.myNodeController);
        };

        Button('position')
          .width(300)
          .onClick(() => {
            renderNode.position = { x: 10, y: 10 };
            hilog.info(DOMAIN, TEST_TAG, ' position:' + JSON.stringify(renderNode.position));
          });
        Button('pivot')
          .width(300)
          .onClick(() => {
            renderNode.pivot = { x: 0.5, y: 0.6 };
            hilog.info(DOMAIN, TEST_TAG, ' pivot:' + JSON.stringify(renderNode.pivot));
          });
        Button('scale')
          .width(300)
          .onClick(() => {
            renderNode.scale = { x: 0.5, y: 1 };
            hilog.info(DOMAIN, TEST_TAG, ' scale:' + JSON.stringify(renderNode.scale));
          });
        Button('translation')
          .width(300)
          .onClick(() => {
            renderNode.translation = { x: 100, y: 0 };
            hilog.info(DOMAIN, TEST_TAG, ' translation:' + JSON.stringify(renderNode.translation));
          });
        Button('rotation')
          .width(300)
          .onClick(() => {
            renderNode.rotation = { x: 45, y: 0, z: 0 };
            hilog.info(DOMAIN, TEST_TAG, ' rotation:' + JSON.stringify(renderNode.rotation));
          });
        Button('transform')
          .width(300)
          .onClick(() => {
            renderNode.transform = [
              1, 0, 0, 0,
              0, 2, 0, 0,
              0, 0, 1, 0,
              0, 0, 0, 1
            ];
            hilog.info(DOMAIN, TEST_TAG, ' transform:' + JSON.stringify(renderNode.transform));
          });
        Button('shadow')
          .width(300)
          .onClick(() => {
            renderNode.shadowElevation = 10;
            renderNode.shadowColor = 0XFF00FF00;
            renderNode.shadowOffset = { x: 10, y: 10 };
            renderNode.shadowAlpha = 0.1;
            hilog.info(DOMAIN, TEST_TAG, ' shadowElevation:' + JSON.stringify(renderNode.shadowElevation));
            hilog.info(DOMAIN, TEST_TAG, ' shadowColor:' + JSON.stringify(renderNode.shadowColor));
            hilog.info(DOMAIN, TEST_TAG, ' shadowOffset:' + JSON.stringify(renderNode.shadowOffset));
            hilog.info(DOMAIN, TEST_TAG, ' shadowAlpha:' + JSON.stringify(renderNode.shadowAlpha));
          });
        Button('shadowRadius')
          .width(300)
          .onClick(() => {
            renderNode.shadowOffset = { x: 10, y: 10 };
            renderNode.shadowAlpha = 0.7;
            renderNode.shadowRadius = 30;
            hilog.info(DOMAIN, TEST_TAG, ' shadowOffset:' + JSON.stringify(renderNode.shadowOffset));
            hilog.info(DOMAIN, TEST_TAG, ' shadowAlpha:' + JSON.stringify(renderNode.shadowAlpha));
            hilog.info(DOMAIN, TEST_TAG, ' shadowRadius:' + JSON.stringify(renderNode.shadowRadius));
          });
        Button('border')
          .width(300)
          .onClick(() => {
            renderNode.borderWidth = {
              left: 8,
              top: 8,
              right: 8,
              bottom: 8
            };
            renderNode.borderStyle = {
              left: BorderStyle.Solid,
              top: BorderStyle.Dotted,
              right: BorderStyle.Dashed,
              bottom: BorderStyle.Solid
            }
            renderNode.borderColor = {
              left: 0xFF0000FF,
              top: 0xFF0000FF,
              right: 0xFF0000FF,
              bottom: 0xFF0000FF
            };
            renderNode.borderRadius = {
              topLeft: 32,
              topRight: 32,
              bottomLeft: 32,
              bottomRight: 32
            };
            hilog.info(DOMAIN, TEST_TAG, ' borderWidth:' + JSON.stringify(renderNode.borderWidth));
            hilog.info(DOMAIN, TEST_TAG, ' borderStyle:' + JSON.stringify(renderNode.borderStyle));
            hilog.info(DOMAIN, TEST_TAG, ' borderColor:' + JSON.stringify(renderNode.borderColor));
            hilog.info(DOMAIN, TEST_TAG, ' borderRadius:' + JSON.stringify(renderNode.borderRadius));
          })
        Button('shapeMask')
          .width(300)
          .onClick(() => {
            renderNode.shapeMask = mask;
            hilog.info(DOMAIN, TEST_TAG, ' shapeMask:' + JSON.stringify(renderNode.shapeMask));
          });
        Button('shapeClip')
          .width(300)
          .onClick(() => {
            renderNode.shapeClip = clip;
            hilog.info(DOMAIN, TEST_TAG, ' shapeClip:' + JSON.stringify(renderNode.shapeClip));
          });
      }
      .padding({
        left: 35,
        right: 35,
        top: 35,
        bottom: 35
      })
      .width('100%')
      .height('100%');

    // ···
  }
}

```

## 自定义绘制

通过重写RenderNode中的[draw](../reference/apis-arkui/js-apis-arkui-renderNode.md#draw)方法，可以自定义RenderNode的绘制内容，通过[invalidate](../reference/apis-arkui/js-apis-arkui-renderNode.md#invalidate)接口可以主动触发节点的重新绘制。

> **说明：**
> 
> - 同时同步触发多个invalidate仅会触发一次重新绘制。
> 
> - 自定义绘制有两种绘制方式：通过ArkTS接口进行调用和通过Node-API进行调用。

**ArkTS接口调用示例：**

<!-- @[custom_draw](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/CustomDraw.ets) -->

## 调整自定义绘制Canvas的变换矩阵

从API version 12开始，通过重写RenderNode中的[draw](../reference/apis-arkui/js-apis-arkui-renderNode.md#draw)方法，可以自定义RenderNode的绘制内容。

通过[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)可以调整自定义绘制Canvas的变换矩阵。

> **说明：**
> 
> - [getTotalMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#gettotalmatrix12)获取的是用来记录绘制指令的临时canvas的变换矩阵。
> 
> - 如果开发者希望对画布进行预期的变换，应使用[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)而不是[setMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#setmatrix12)，因为setMatrix会覆盖原本真实canvas上存在的变换矩阵。

**ArkTS接口调用示例：**

<!-- @[custom_draw_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/CustomDrawCanvas.ets) -->

![RenderNode-canvas](./figures/renderNode-canvas.png)

**Node-API调用示例：**

C++侧可通过Node-API来获取Canvas，并进行后续的自定义绘制操作。

<!-- @[native_bridge](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/cpp/NativeBridge.cpp) -->

修改工程中的`src/main/cpp/CMakeLists.txt`文件，添加如下内容：
```cmake
# the minimum version of CMake.
cmake_minimum_required(VERSION 3.4.1)
project(NapiTest)

set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${NATIVERENDER_ROOT_PATH}
                    ${NATIVERENDER_ROOT_PATH}/include)

add_library(entry SHARED NativeBridge.cpp)
target_link_libraries(entry PUBLIC libace_napi.z.so)
target_link_libraries(entry PUBLIC libace_ndk.z.so)
target_link_libraries(entry PUBLIC libnative_drawing.so)
```

同时在工程中的`src/main/cpp/types/libentry/index.d.ts`文件中，添加自定义绘制函数在ArkTS侧的定义，如：
<!-- @[index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/cpp/types/libentry/Index.d.ts) -->

ArkTS侧代码：

<!-- @[custom_draw_canvas_native](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/CustomDrawCanvasNative.ets) -->

## 设置标签

开发者可利用[label](../reference/apis-arkui/js-apis-arkui-renderNode.md#label12)接口向RenderNode设置标签信息，这有助于在节点Inspector中更清晰地区分各节点。

<!-- @[set_label](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/SetLabel.ets) -->

## 查询当前RenderNode是否解除引用

前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。

从API version 20开始，使用[isDisposed](../reference/apis-arkui/js-apis-arkui-renderNode.md#isdisposed20)接口查询当前RenderNode对象是否已解除与后端实体节点的引用关系，从而可以在操作节点前检查其有效性，避免潜在风险。

<!-- @[check_rander_node_disposed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/CustomRenderNode/entry/src/main/ets/pages/CheckRanderNodeDisposed.ets) -->