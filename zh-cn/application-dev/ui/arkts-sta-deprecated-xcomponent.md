# UI组件适配（XComponent）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## setXComponentSurfaceSize

ArkTS-Dyn接口声明：[setXComponentSurfaceSize(value: {surfaceWidth: number, surfaceHeight: number}): void](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#setXComponentSurfaceSizedeprecated)

替代的ArkTS-Sta接口声明：[setXComponentSurfaceRect(rect: SurfaceRect): void](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#setxcomponentsurfacerect12)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct XComponentExample {
  xComponentController: XComponentController = new XComponentController();

  build() {
    Column() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
        .onClick(() => {
          this.xComponentController.setXComponentSurfaceSize({ surfaceWidth: 100, surfaceHeight: 100 });
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct XComponentExample {
  xComponentController: XComponentController = new XComponentController();

  build() {
    Column() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
        .onClick(() => {
          this.xComponentController.setXComponentSurfaceRect({ surfaceWidth: 100, surfaceHeight: 100 } as SurfaceRect);
        })
    }
  }
}
```

## XComponent

ArkTS-Dyn接口声明：[XComponent(value: {id: string, type: string, libraryname?: string, controller?: XComponentController})](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#xcomponentdeprecated)

替代的ArkTS-Sta接口声明：[XComponent(options: XComponentOptions)](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#xcomponent12)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct XComponentExample {
  build() {
    Column() {
      XComponent({
        id: 'xc',
        type: 'surface'
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct XComponentExample {
  build() {
    Column() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: new XComponentController()
      } as XComponentOptions)
    }
  }
}
```

## XComponentType

### XComponentType.COMPONENT

ArkTS-Dyn接口声明：[XComponentType.COMPONENT](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#xcomponenttype10)

替代的ArkTS-Sta接口声明：[Column(options?: ColumnOptions)](../reference/apis-arkui/arkui-ts/ts-container-column.md#column-1)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct XComponentExample {
  build() {
    Column() {
      XComponent({ type: XComponentType.COMPONENT }) {
        Text('hello world');
      }
    }
  }
}
```

ArkTS-Sta示例：

```ts
@Entry
@Component
struct XComponentExample {
  build() {
    Column() {
      Column() {
        Text('hello world');
      }
    }
  }
}
```

### XComponentType.NODE

ArkTS-Dyn接口声明：[XComponentType.NODE](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#xcomponenttype10)

替代的ArkTS-Sta接口声明：[ArkTS侧接口：ContentSlot(content: Content)](state-management/arkts-rendering-control-contentslot.md#arkts侧接口)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct XComponentExample {
  build() {
    Column() {
      XComponent({ id: 'xc', type: XComponentType.NODE });
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { NodeContent } from '@kit.ArkUI';

@Entry
@Component
struct XComponentExample {
  private nodeContent: Content = new NodeContent();

  build() {
    Column() {
      ContentSlot(this.nodeContent);
    }
  }
}
```

## XComponentNode

### constructor

ArkTS-Dyn接口声明：[constructor(uiContext: UIContext, options: RenderOptions, id: string, type: XComponentType, libraryName?: string)](../reference/apis-arkui/js-apis-arkui-xcomponentNode.md#constructor)

替代的ArkTS-Sta接口声明：[createNode(context: UIContext, nodeType: 'XComponent'): XComponent](../reference/apis-arkui/js-apis-arkui-frameNode.md#createnodexcomponent12)



ArkTS-Dyn示例：

```ts
import { XComponentNode, NodeController } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  private xComponentNode: MyXComponentNode | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.xComponentNode =
      new MyXComponentNode(context, { selfIdealSize: { width: 200, height: 200 } }, "xc", XComponentType.SURFACE);
    return this.xComponentNode;
  }
}

class MyXComponentNode extends XComponentNode {
}
```

ArkTS-Sta示例：

```ts
import { NodeController, typeNode } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  makeNode(context: UIContext): FrameNode | null {
    let opt: XComponentOptions =
      { type: XComponentType.SURFACE, controller: new XComponentController() } as XComponentOptions;
    let node = typeNode.createNode(context, 'XComponent', opt);
    return node;
  }
}
```

### onCreate

ArkTS-Dyn接口声明：[onCreate(event?: Object): void](../reference/apis-arkui/js-apis-arkui-xcomponentNode.md#oncreate)

替代的ArkTS-Sta接口声明：[onSurfaceCreated(surfaceId: string): void](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#onsurfacecreated12)



ArkTS-Dyn示例：

```ts
import { XComponentNode, NodeController } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  private xComponentNode: MyXComponentNode | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.xComponentNode =
      new MyXComponentNode(context, { selfIdealSize: { width: 200, height: 200 } }, "xc", XComponentType.SURFACE);
    return this.xComponentNode;
  }
}

class MyXComponentNode extends XComponentNode {
  onCreate() {
    console.log('onCreate');
  }
}
```

ArkTS-Sta示例：

```ts
import { NodeController, typeNode } from '@kit.ArkUI';

class MyXComponentController extends XComponentController {
  onSurfaceCreated(surfaceId: string): void {
    console.log('onCreate');
  }
}

class XComponentNodeController extends NodeController {
  makeNode(context: UIContext): FrameNode | null {
    let opt: XComponentOptions =
      { type: XComponentType.SURFACE, controller: new MyXComponentController() } as XComponentOptions;
    let node = typeNode.createNode(context, 'XComponent', opt);
    return node;
  }
}
```

### onDestroy

ArkTS-Dyn接口声明：[onDestroy(): void](../reference/apis-arkui/js-apis-arkui-xcomponentNode.md#ondestroy)

替代的ArkTS-Sta接口声明：[onDestroy(event: VoidCallback): XComponentAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md#ondestroy)



ArkTS-Dyn示例：

```ts
import { XComponentNode, NodeController } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  private xComponentNode: MyXComponentNode | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.xComponentNode =
      new MyXComponentNode(context, { selfIdealSize: { width: 200, height: 200 } }, "xc", XComponentType.SURFACE);
    return this.xComponentNode;
  }
}

class MyXComponentNode extends XComponentNode {
  onDestroy() {
    console.log('onDestroy');
  }
}
```

ArkTS-Sta示例：

```ts
import { NodeController, typeNode } from '@kit.ArkUI';

class XComponentNodeController extends NodeController {
  makeNode(context: UIContext): FrameNode | null {
    let opt: XComponentOptions =
      { type: XComponentType.SURFACE, controller: new XComponentController() } as XComponentOptions;
    let node = typeNode.createNode(context, 'XComponent', opt);
    node.attribute.onDestroy(() => {
      console.log('onDestroy');
    })
    return node;
  }
}
```

### changeRenderType

ArkTS-Dyn接口声明：[changeRenderType(type: NodeRenderType): boolean](../reference/apis-arkui/js-apis-arkui-xcomponentNode.md#changeRenderType)

替代的ArkTS-Sta接口声明：[constructor(uiContext: UIContext, options?: RenderOptions)](../reference/apis-arkui/js-apis-arkui-builderNode.md#constructor)



ArkTS-Dyn示例：

```ts
import { XComponentNode, NodeRenderType, UIContext } from '@kit.ArkUI';

class MyNodeController {
  testChangeRenderType(context: UIContext): void {
    let node = new XComponentNode(context, {}, 'xc', XComponentType.SURFACE);
    node.changeRenderType(NodeRenderType.RENDER_TYPE_TEXTURE);
  }
}
```

ArkTS-Sta示例：

```ts
import { BuilderNode, RenderOptions, NodeRenderType, UIContext } from '@kit.ArkUI';

class MyNodeController {
  testChangeRenderType(context: UIContext): void {
    let node = new BuilderNode(context, { type: NodeRenderType.RENDER_TYPE_TEXTURE } as RenderOptions);
  }
}
```