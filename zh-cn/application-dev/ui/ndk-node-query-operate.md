# 查询和操作自定义节点
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

NDK提供一系列节点查询、遍历、操作能力，通过使用以下接口，开发者可以高效地访问和操控节点。

以下场景基于[接入ArkTS页面](ndk-access-the-arkts-page.md)章节，创建前置工程。

## 查询节点uniqueId及通过uniqueId获取节点信息

uniqueId是系统分配的唯一标识的节点Id。

从API version 20开始，使用[OH_ArkUI_NodeUtils_GetNodeUniqueId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getnodeuniqueid)接口，可以获取目标节点的uniqueId。使用[OH_ArkUI_NodeUtils_GetNodeHandleByUniqueId](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getnodehandlebyuniqueid)接口，可以通过uniqueId获取目标节点的指针。

<!-- @[ndknodequeryoperate1_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/InquireUniqueId.cpp) -->

## 通过用户id获取节点信息

使用[OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid)接口，可以通过用户设置的id获取目标节点的指针。

1. ArkTS侧接入Native组件。

<!-- @[ndknodequeryoperate2_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/ets/pages/GetNodeById.ets) -->

2. 新建`GetNodeByIdExample.h`文件，在其中创建Text节点并设置id属性，通过OH_ArkUI_NodeUtils_GetAttachedNodeHandleById接口拿到节点。

<!-- @[ndknodequeryoperate3_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/GetNodeByIdExample.h) -->

3. 在`NativeEntry.cpp`中，挂载Native节点。

<!-- @[ndknodequeryoperate3_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/NativeEntry.cpp) -->

4. 运行程序，点击按钮，打印节点获取成功信息。

## 移动节点

使用[OH_ArkUI_NodeUtils_MoveTo](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_moveto)接口，可以将Native节点移动到新的父节点下，从而按需改变节点树结构。

> **说明：**
>
> 当前仅支持以下类型的[ArkUI_NodeType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodetype)进行移动操作：ARKUI_NODE_STACK、ARKUI_NODE_XCOMPONENT、ARKUI_NODE_EMBEDDED_COMPONENT。对于其他类型的节点，移动操作不会生效。

1. ArkTS侧接入Native组件。

<!-- @[ndknodequeryoperate4_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/ets/pages/MoveTo.ets) -->

2. 新建`MoveTo.h`文件，在其中创建Stack节点，通过OH_ArkUI_NodeUtils_MoveTo接口移动Stack节点。

<!-- @[ndknodequeryoperate5_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/MoveToExample.h) -->

3. 在`NativeEntry.cpp`中，挂载Native节点。

<!-- @[ndknodequeryoperate3_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/NativeEntry.cpp) -->

4. 运行程序，点击按钮，Stack节点会移动到目标位置。

![moveToNativeDemo](figures/moveToNativeDemo.gif)

## 在当前即时帧触发节点属性更新

从API version 21开始，使用[OH_ArkUI_NativeModule_InvalidateAttributes](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nativemodule_invalidateattributes)接口，在当前帧即时触发节点属性更新，避免组件切换过程中出现闪烁。

1. ArkTS侧接入Native组件。

<!-- @[ndknodequeryoperate6_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/ets/pages/Attribute.ets) -->

2. 新建`Attribute_util .h`用于设置组件属性。

<!-- @[ndknodequeryoperate7_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/Attribute_util.h) -->

3. 在`nai_init.cpp`中，挂载Native节点。

<!-- @[ndknodequeryoperate7_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/napi_init.cpp) -->

4. 运行程序，点击按钮，切换图片正常展示。

![moveToNativeDemo](figures/OH_ArkUI_NativeModule_InvalidateAttributes_test.png)

## 用不同的展开模式获取对应下标的子节点

NDK支持通过不同的展开方式获取目标节点下的有效节点信息。例如，在LazyForEach场景下，可以处理存在多个子节点的情况。

从API version 20开始，使用[OH_ArkUI_NodeUtils_GetFirstChildIndexWithoutExpand](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getfirstchildindexwithoutexpand)接口，可以获取目标节点的第一个存在于组件树的节点。使用[OH_ArkUI_NodeUtils_GetLastChildIndexWithoutExpand](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getlastchildindexwithoutexpand)接口，可以获取目标节点的最后一个存在于组件树的节点。[OH_ArkUI_NodeUtils_GetChildWithExpandMode](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getchildwithexpandmode)接口，可以通过不同的节点展开模式获取对应下标的子节点。

> **说明：**
>
> 节点展开方式请参考[ArkUI_ExpandMode](../reference/apis-arkui/capi-native-type-h.md#arkui_expandmode)，此处推荐使用ARKUI_LAZY_EXPAND懒展开方式，智能识别对应场景。

1. 通过ArkTS构造LazyForEach及ArkTS的下树节点展开场景。

    ```ts
    import { NodeController, FrameNode, UIContext, BuilderNode, ExpandMode, LengthUnit } from '@kit.ArkUI';
    
    const TEST_TAG: string = "FrameNode ";
    
    // BasicDataSource实现了IDataSource接口，用于管理listener监听，以及通知LazyForEach数据更新
    class BasicDataSource implements IDataSource {
      private listeners: DataChangeListener[] = [];
      private originDataArray: string[] = [];
    
      public totalCount(): number {
        return 0;
      }
    
      public getData(index: number): string {
        return this.originDataArray[index];
      }
    
      // 该方法为框架侧调用，为LazyForEach组件向其数据源处添加listener监听
      registerDataChangeListener(listener: DataChangeListener): void {
        if (this.listeners.indexOf(listener) < 0) {
          console.info('add listener');
          this.listeners.push(listener);
        }
      }
    
      // 该方法为框架侧调用，为对应的LazyForEach组件在数据源处去除listener监听
      unregisterDataChangeListener(listener: DataChangeListener): void {
        const pos = this.listeners.indexOf(listener);
        if (pos >= 0) {
          console.info('remove listener');
          this.listeners.splice(pos, 1);
        }
      }
    
      // 通知LazyForEach组件需要重载所有子组件
      notifyDataReload(): void {
        this.listeners.forEach(listener => {
          listener.onDataReloaded();
        })
      }
    
      // 通知LazyForEach组件需要在index对应索引处添加子组件
      notifyDataAdd(index: number): void {
        this.listeners.forEach(listener => {
          listener.onDataAdd(index);
          // 写法2：listener.onDatasetChange([{type: DataOperationType.ADD, index: index}]);
        })
      }
    
      // 通知LazyForEach组件在index对应索引处数据有变化，需要重建该子组件
      notifyDataChange(index: number): void {
        this.listeners.forEach(listener => {
          listener.onDataChange(index);
          // 写法2：listener.onDatasetChange([{type: DataOperationType.CHANGE, index: index}]);
        })
      }
    
      // 通知LazyForEach组件需要在index对应索引处删除该子组件
      notifyDataDelete(index: number): void {
        this.listeners.forEach(listener => {
          listener.onDataDelete(index);
          // 写法2：listener.onDatasetChange([{type: DataOperationType.DELETE, index: index}]);
        })
      }
    
      // 通知LazyForEach组件将from索引和to索引处的子组件进行交换
      notifyDataMove(from: number, to: number): void {
        this.listeners.forEach(listener => {
          listener.onDataMove(from, to);
          // 写法2：listener.onDatasetChange(
          //         [{type: DataOperationType.EXCHANGE, index: {start: from, end: to}}]);
        })
      }
    
      notifyDatasetChange(operations: DataOperation[]): void {
        this.listeners.forEach(listener => {
          listener.onDatasetChange(operations);
        })
      }
    }
    
    class MyDataSource extends BasicDataSource {
      private dataArray: string[] = []
    
      public totalCount(): number {
        return this.dataArray.length;
      }
    
      public getData(index: number): string {
        return this.dataArray[index];
      }
    
      public addData(index: number, data: string): void {
        this.dataArray.splice(index, 0, data);
        this.notifyDataAdd(index);
      }
    
      public pushData(data: string): void {
        this.dataArray.push(data);
        this.notifyDataAdd(this.dataArray.length - 1);
      }
    }
    
    class Params {
      data: MyDataSource | null = null;
      scroller: Scroller | null = null;
      constructor(data: MyDataSource, scroller: Scroller) {
        this.data = data;
        this.scroller = scroller;
      }
    }
    
    @Builder
    function buildData(params: Params) {
      List({ scroller: params.scroller }) {
        LazyForEach(params.data, (item: string) => {
          ListItem() {
            Column() {
              Text(item)
                .fontSize(20)
                .onAppear(() => {
                  console.info(TEST_TAG + " node appear: " + item)
                })
                .backgroundColor(Color.Pink)
                .margin({
                  top: 30,
                  bottom: 30,
                  left: 10,
                  right: 10
                })
            }
          }
          .id(item)
        }, (item: string) => item)
      }
      .cachedCount(5)
      .listDirection(Axis.Horizontal)
    }
    
    class MyNodeController extends NodeController {
      private rootNode: FrameNode | null = null;
      private uiContext: UIContext | null = null;
      private data: MyDataSource = new MyDataSource();
      private scroller: Scroller = new Scroller();
    
      makeNode(uiContext: UIContext): FrameNode | null {
        this.uiContext = uiContext;
        for (let i = 0; i <= 20; i++) {
          this.data.pushData(`N${i}`);
        }
        const params: Params = new Params(this.data, this.scroller);
        const dataNode: BuilderNode<[Params]> = new BuilderNode(uiContext);
        dataNode.build(wrapBuilder<[Params]>(buildData), params);
        this.rootNode = dataNode.getFrameNode();
        const scrollToIndexOptions: ScrollToIndexOptions = {
          extraOffset: {
            value: 20, unit: LengthUnit.VP
          }
        };
        this.scroller.scrollToIndex(6, true, ScrollAlign.START, scrollToIndexOptions);
        return this.rootNode;
      }

      // 获取不展开场景下第一个活跃节点的下标
      getFirstChildIndexWithoutExpand() {
        console.info(`${TEST_TAG} getFirstChildIndexWithoutExpand: ${this.rootNode!.getFirstChildIndexWithoutExpand()}`);
      }

      // 获取不展开场景下最后一个活跃节点的下标
      getLastChildIndexWithoutExpand() {
        console.info(`${TEST_TAG} getLastChildIndexWithoutExpand: ${this.rootNode!.getLastChildIndexWithoutExpand()}`);
      }

      // 用不展开的方式获取节点
      getChildWithNotExpand() {
        const childNode = this.rootNode!.getChild(3, ExpandMode.NOT_EXPAND);
        console.info(TEST_TAG + " getChild(3, ExpandMode.NOT_EXPAND): " + childNode?.getId());
        if (childNode?.getId() === "N9") {
          console.info(TEST_TAG + " getChild(3, ExpandMode.NOT_EXPAND)  result: success.");
        } else {
          console.info(TEST_TAG + " getChild(3, ExpandMode.NOT_EXPAND)  result: fail.");
        }
      }
      
      // 以展开的方式获取节点
      getChildWithExpand() {
        const childNode = this.rootNode!.getChild(3, ExpandMode.EXPAND);
        console.info(TEST_TAG + " getChild(3, ExpandMode.EXPAND): " + childNode?.getId());
        if (childNode?.getId() === "N3") {
          console.info(TEST_TAG + " getChild(3, ExpandMode.EXPAND)  result: success.");
        } else {
          console.info(TEST_TAG + " getChild(3, ExpandMode.EXPAND)  result: fail.");
        }
      }
      
      getChildWithLazyExpand() {
        const childNode = this.rootNode!.getChild(3, ExpandMode.LAZY_EXPAND);
        console.info(TEST_TAG + " getChild(3, ExpandMode.LAZY_EXPAND): " + childNode?.getId());
        if (childNode?.getId() === "N3") {
          console.info(TEST_TAG + " getChild(3, ExpandMode.LAZY_EXPAND)  result: success.");
        } else {
          console.info(TEST_TAG + " getChild(3, ExpandMode.LAZY_EXPAND)  result: fail.");
        }
      }
    }
    
    @Entry
    @Component
    struct Index {
      private myNodeController: MyNodeController = new MyNodeController();
      private scroller: Scroller = new Scroller();
    
      build() {
        Scroll(this.scroller) {
          Column({ space: 8 }) {
            Column() {
              Text("This is a NodeContainer.")
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
                .width('100%')
                .fontSize(16)
              NodeContainer(this.myNodeController)
                .borderWidth(1)
                .width(300)
                .height(100)
            }
    
            Button("getFirstChildIndexWithoutExpand")
                .width(300)
                .onClick(() => {
                  this.myNodeController.getFirstChildIndexWithoutExpand();
                })
              Button("getLastChildIndexWithoutExpand")
                .width(300)
                .onClick(() => {
                  this.myNodeController.getLastChildIndexWithoutExpand();
                })
              Button("getChildWithNotExpand")
                .width(300)
                .onClick(() => {
                  this.myNodeController.getChildWithNotExpand();
                })
              Button("getChildWithExpand")
                .width(300)
                .onClick(() => {
                  this.myNodeController.getChildWithExpand();
                })
              Button("getChildWithLazyExpand")
                .width(300)
                .onClick(() => {
                  this.myNodeController.getChildWithLazyExpand();
                })
            }
            .width("100%")
          }
          .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
        }
      }
    ```
  
2. NDK侧通过[OH_ArkUI_NodeUtils_GetAttachedNodeHandleById](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeutils_getattachednodehandlebyid)接口获取ArkTS组件，并通过懒展开模式获取对应的子组件信息。

<!-- @[ndknodequeryoperate9_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NdkNodeQueryOperate/entry/src/main/cpp/ShowSubcomponentInfo.h) -->

3. 查看日志打印的对应错误码返回是否正确，以此判断是否成功获取到对应子节点。
