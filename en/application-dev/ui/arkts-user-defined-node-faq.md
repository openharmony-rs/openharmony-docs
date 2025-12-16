# Custom Node FAQs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

This topic addresses common issues related to custom nodes.

## Delayed aboutToDisappear Callback in Custom Components

**Symptom**

Starting from API version 12, the [aboutToDisappear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear) method of a custom component is not triggered immediately after the component's child nodes exit the page. The **aboutToDisappear** method of a custom component is usually triggered when the component is destroyed.

**Possible Causes**

- The custom component has a parent node that remains undestroyed.
- The custom component is created via [BuilderNode](./arkts-user-defined-arktsNode-builderNode.md). By default, BuilderNode holds a strong reference to the backend node, so the frontend object is neither reclaimed nor removed from the backend component's reference list.
- Calling [OH_ArkUI_GetNodeHandleFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getnodehandlefromnapivalue) to obtain the root node of a **BuilderNode** or **ComponentContent** object increases the backend node's reference count by 1.
- In [NodeContent](../reference/apis-arkui/js-apis-arkui-NodeContent.md), using [addFrameNode](../reference/apis-arkui/js-apis-arkui-NodeContent.md#addframenode12) to add a FrameNode creates a reference relationship. If the **NodeContent** object is not reclaimed and [removeFrameNode](../reference/apis-arkui/js-apis-arkui-NodeContent.md#removeframenode12) is not called, the reference persists.

**Solution**

- Remove the custom component to be released from its parent node to eliminate the parent node's impact on the component's lifecycle.
- For custom components created using [BuilderNode](./arkts-user-defined-arktsNode-builderNode.md), call [dispose](../reference/apis-arkui/js-apis-arkui-builderNode.md#dispose12) to immediately release the frontend BuilderNode's strong reference to the backend node.
- For root nodes obtained via **OH_ArkUI_GetNodeHandleFromNapiValue** (from **BuilderNode** or **ComponentContent**),
call [disposenode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#disposenode) to decrease the reference count increased by **OH_ArkUI_GetNodeHandleFromNapiValue**.
- If **dispose** is not called, the frontend BuilderNode object will be reclaimed during [garbage collection (GC)](../arkts-utils/gc-introduction.md), and the reference to the backend root node will be released. For debugging, use the [hidumper](../dfx/hidumper.md) command to trigger GC or [query heap memory](../dfx/hidumper.md#querying-vm-heap-memory) to analyze reference relationships.

**Sample Code**

In the following example, the root node indicates the root node of BuilderNode, and **aboutToDisappear** refers to the callback in the custom component (**BuilderNodePage**) built with BuilderNode.

- After displaying and navigating back from the pageOneTmp page, trigger GC via command. The **aboutToDisappear** callback will be logged after device operation. Reference management:
  - NodeContent to the root node: Recycle the **NodeContent** object or call the **removeFrameNode()** API.
  - Global object to BuilderNode: Clear [ArrayList](../reference/apis-arkts/js-apis-arraylist.md) references using the [clear](../reference/apis-arkts/js-apis-arraylist.md#clear) method.
  - BuilderNode object to the root node: Ensure that no other references to the BuilderNode object exist. Triggering object recycling will release the root node reference.

- After you navigate to and then return from the **pageTwoTmp** page, the **aboutToDisappear** callback is triggered and logged. Reference management:
  - NodeContent to the root node: Explicitly call the **removeFrameNode** API of **NodeContent**.
  - BuilderNode object to the root node: Directly call the **dispose** API of **BuilderNode**.

- After you navigate to and then return from the **pageThreeTmp** page, the **aboutToDisappear** callback is triggered and logged. Reference management:
  - Parent FrameNode to the root node: Call the **removeChild** API of **FrameNode** to detach from the parent node.
  - BuilderNode object to the root node: Directly call the **dispose** API of **BuilderNode**.

```ts

import { BuilderNode, FrameNode, NodeContent } from '@kit.ArkUI';
import { ArrayList } from '@kit.ArkTS';

const CUSTOM_COMPONENT_CONT: string = "CustomComponentCont"
AppStorage.setOrCreate<number>(CUSTOM_COMPONENT_CONT, 0);
let globalBuilderNodeList: ArrayList<BuilderNode<[]>> = new ArrayList<BuilderNode<[]>>();

@Component
struct BuilderNodePage {
  aboutToAppear(): void {
    const count: number | undefined = AppStorage.get<number>(CUSTOM_COMPONENT_CONT);
    const current: number = count ? count + 1 : 1;
    AppStorage.setOrCreate<number>(CUSTOM_COMPONENT_CONT, current);
    console.info("BuilderNodePage", "aboutToAppear " + AppStorage.get<number>(CUSTOM_COMPONENT_CONT))
  }

  aboutToDisappear(): void {
    setTimeout(() => {
      const count: number | undefined = AppStorage.get<number>(CUSTOM_COMPONENT_CONT);
      console.info("BuilderNodePage", "aboutToDisappear " + count)
      const current: number = count ? count - 1 : -1;
      AppStorage.set<number>(CUSTOM_COMPONENT_CONT, current)
      console.info("BuilderNodePage", "aboutToDisappear " + AppStorage.get<number>(CUSTOM_COMPONENT_CONT))
    }, 1)
  }

  build() {
    Text("This is a BuilderNode")
  }
}

@Builder
function BuilderNodeBuilder() {
  BuilderNodePage();
}

@Entry
@Component
struct NavigationExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack()
  private arr: number[] = [1, 2, 3];
  @StorageProp(CUSTOM_COMPONENT_CONT) customComponentCount: number | undefined =
    AppStorage.get<number>(CUSTOM_COMPONENT_CONT);

  @Builder
  pageMap(name: string) {
    if (name === "NavDestinationTitle1") {
      pageOneTmp();
    } else if (name === "NavDestinationTitle2") {
      pageTwoTmp();
    } else if (name === "NavDestinationTitle3") {
      pageThreeTmp();
    }
  }

  onPageShow(): void {
    console.info("NavigationExample " + this.customComponentCount);
  }

  build() {
    Column() {
      Navigation(this.pageInfos) {
        Text("Number of remaining custom components in BuilderNode: " + this.customComponentCount)
          .width("90%")
          .height(40)
          .backgroundColor('#FFFFFF')
        Button("Remove Global References")
          .onClick(() => {
            // Remove all global references.
            // Trigger GC using hidumper commands to verify reference cleanup.
            globalBuilderNodeList.clear();
          })
        List({ space: 12 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text("Page" + item)
                .width("100%")
                .height(72)
                .backgroundColor('#FFFFFF')
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
                .onClick(() => {
                  this.pageInfos.pushPath({ name: "NavDestinationTitle" + item });
                })
            }
          }, (item: number) => item.toString())
        }
        .width("100%")
        .margin({ top: 12 })
      }
      .title("Main Title")
      .mode(NavigationMode.Stack)
      .navDestination(this.pageMap)
    }
    .height('100%')
    .width('100%')
    .backgroundColor('#F1F3F5')
  }
}

// PageOne.ets
@Component
export struct pageOneTmp {
  @Consume('pageInfos') pageInfos: NavPathStack;
  private builderNode: BuilderNode<[]> = new BuilderNode(this.getUIContext());
  private content: NodeContent = new NodeContent();

  aboutToAppear(): void {
    console.info("pageOneTmp", "aboutToAppear")
    this.builderNode.build(wrapBuilder(BuilderNodeBuilder));
    if (this.builderNode.getFrameNode()) {
      this.content.addFrameNode(this.builderNode.getFrameNode());
    }
    // Add a global reference, which prevents GC until it is removed.
    globalBuilderNodeList.add(this.builderNode);
  }

  aboutToDisappear(): void {
    console.info("pageOneTmp", "aboutToDisappear")
  }

  build() {
    NavDestination() {
      Column() {
        Text("pageOneTmp")
        ContentSlot(this.content)
      }.width('100%').height('100%')
    }.title("NavDestinationTitle1")
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top element from the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

// PageTwo.ets
@Component
export struct pageTwoTmp {
  @Consume('pageInfos') pageInfos: NavPathStack;
  private builderNode: BuilderNode<[]> = new BuilderNode(this.getUIContext());
  private content: NodeContent = new NodeContent();

  aboutToAppear(): void {
    console.info("pageTwoTmp", "aboutToAppear")
    this.builderNode!.build(wrapBuilder(BuilderNodeBuilder));
    if (this.builderNode!.getFrameNode()) {
      // Mount the root node of BuilderNode to the NodeContent object.
      // To destroy the root node of BuilderNode, remove it from the NodeContent object or wait for NodeContent GC.
      // Otherwise, the root node of BuilderNode cannot be destroyed.
      this.content.addFrameNode(this.builderNode!.getFrameNode());
    }
  }

  aboutToDisappear(): void {
    console.info("pageTwoTmp", "aboutToDisappear")
    if (this.builderNode?.getFrameNode()) {
      // Remove the root node of BuilderNode from the NodeContent object.
      // This API must be called before the dispose API of BuilderNode. Otherwise, the root node of BuilderNode cannot be obtained.
      this.content.removeFrameNode(this.builderNode?.getFrameNode());
    }
    this.builderNode?.dispose();
  }

  build() {
    NavDestination() {
      Column() {
        Text("pageTwoTmp")
        ContentSlot(this.content)
      }.width('100%').height('100%')
    }.title("NavDestinationTitle2")
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top element from the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

// PageThree.ets
@Component
export struct pageThreeTmp {
  @Consume('pageInfos') pageInfos: NavPathStack;
  private builderNode: BuilderNode<[]> = new BuilderNode(this.getUIContext());
  private content: NodeContent = new NodeContent();
  private rootNode: FrameNode = new FrameNode(this.getUIContext());

  aboutToAppear(): void {
    console.info("pageThreeTmp", "aboutToAppear")
    this.builderNode!.build(wrapBuilder(BuilderNodeBuilder));
    if (this.builderNode!.getFrameNode()) {
      this.content.addFrameNode(this.rootNode);
      // Mount the root node of BuilderNode to the node corresponding to the FrameNode object.
      // To destroy the root node of BuilderNode, remove it from the node corresponding to the FrameNode object or wait for FrameNode destruction.
      // Otherwise, the root node of BuilderNode cannot be destroyed.
      this.rootNode.appendChild(this.builderNode.getFrameNode());
    }
  }

  aboutToDisappear(): void {
    console.info("pageThreeTmp", "aboutToDisappear")
    if (this.builderNode?.getFrameNode()) {
      // Remove the root node of BuilderNode from the node corresponding to the FrameNode object.
      // This API must be called before the dispose API of BuilderNode and the dispose API of FrameNode. Otherwise, the nodes corresponding to BuilderNode and FrameNode cannot be obtained.
      this.rootNode.removeChild(this.builderNode?.getFrameNode());
    }
    this.builderNode?.dispose();
  }

  build() {
    NavDestination() {
      Column() {
        Text("pageThreeTmp")
        ContentSlot(this.content)
      }.width('100%').height('100%')
    }.title("NavDestinationTitle3")
    .onBackPressed(() => {
      const popDestinationInfo = this.pageInfos.pop(); // Pop the top element from the route stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

```
