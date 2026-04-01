# ArkUI子系统Changelog

## cl.arkui.1 NodeAdapter的onAttachToNode回调触发时机变更

**访问级别**

公共能力

**变更原因**

NodeAdapter绑定的宿主节点在主树挂载时，会触发[onAttachToNode](../../../application-dev/reference/apis-arkui/js-apis-arkui-frameNode.md#onattachtonode12)回调，或触发[OH_ArkUI_NodeAdapter_RegisterEventReceiver](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeadapter_registereventreceiver)绑定的、事件类型为[NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeadaptereventtype)的回调，与文档描述的在绑定时触发回调的时机不符。

**变更影响**

变更前：NodeAdapter所绑定的宿主节点上主树时，触发NodeAdapter的onAttachToNode回调，或触发OH_ArkUI_NodeAdapter_RegisterEventReceiver绑定的、事件类型为NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE的回调。

变更后：NodeAdapter被绑定到宿主节点时，触发onAttachToNode的回调，或触发OH_ArkUI_NodeAdapter_RegisterEventReceiver绑定的、事件类型为NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE的回调。

**起始 API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.20开始。

**变更的接口/组件**

[onAttachToNode](../../../application-dev/reference/apis-arkui/js-apis-arkui-frameNode.md#onattachtonode12)

[OH_ArkUI_NodeAdapter_RegisterEventReceiver](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeadapter_registereventreceiver)

**适配指导**

- onAttachToNode触发时节点未上树

  在使用[attachNodeAdapter](../../../application-dev/reference/apis-arkui/js-apis-arkui-frameNode.md#attachnodeadapter12)接口为FrameNode绑定NodeAdapter时，节点可能尚未完全挂载。因此，建议在FrameNode绑定NodeAdapter时的onAttachToNode回调中，注册[onAppear](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear)，并将访问布局信息或执行动画等强依赖主树的操作放入其中，避免因节点未上树引发的执行异常。
 
    ```ts
    
    import { NodeAdapter, NodeController, FrameNode, typeNode, UIContext } from '@kit.ArkUI';
    import hilog from '@ohos.hilog';
    
    class MyNodeAdapter extends NodeAdapter {
      private rootNode: FrameNode | undefined;
    
      setRootNode(node: FrameNode) {
        this.rootNode = node;
      }
    
      // 从API版本26.0.0开始，当NodeAdapter绑定到宿主节点时，会调用如下回调
      onAttachToNode(): void {
        // 适配前：直接在此处执行依赖主树的逻辑，可能因节点未上树引发执行异常
        // this.doWhenNodeAttached();
    
        // 适配后：通过onAppear确保节点已挂载
        this.rootNode?.commonEvent.setOnAppear(() => {
          this.doWhenNodeAttached();
        });
      }
    
      private doWhenNodeAttached() {
        hilog.info(0x0000, 'testTag', 'Node is now attached to main tree');
      }
    }
    
    class MyNodeController extends NodeController {
      private adapter: MyNodeAdapter | undefined;
    
      makeNode(uiContext: UIContext): FrameNode | null {
        this.adapter = new MyNodeAdapter();
        const rootNode = typeNode.createNode(uiContext, 'List');
        rootNode.commonAttribute.width(200).height(200);
    
        // 将宿主节点传递给adapter，以便在onAttachToNode中注册onAppear
        this.adapter.setRootNode(rootNode);
    
        // 绑定adapter，此时会触发onAttachToNode回调
        NodeAdapter.attachNodeAdapter(this.adapter, rootNode);
    
        return rootNode;
      }
    }
    
    ```

- onAttachToNode回调在attachNodeAdapter前设置

  变更前，onAttachToNode生命周期回调，是在通过attachNodeAdapter接口将节点成功挂载到主树之后触发，因此attachNodeAdapter的调用与onAttachToNode回调函数的设置之间并无严格的时序要求。变更后，调用attachNodeAdapter后会立即触发onAttachToNode回调。因此变更后必须在调用attachNodeAdapter之前，设置onAttachToNode回调，否则将导致回调无法被触发，适配指导如下。

    ```ts
    
     import { FrameNode, NodeAdapter, NodeController, typeNode, UIContext } from '@kit.ArkUI';
    
     class NodeAdapterTest extends NodeAdapter {
      uiContext:UIContext;
      frameNodeList:Array<FrameNode> = new Array();
      totalNodeCount_:number;
      public onAttachToNodeFunc:undefined|Function = undefined;
      constructor(uiContext:UIContext) {
        super();
        this.uiContext = uiContext;
        this.totalNodeCount_ = 10;
        this.totalNodeCount = this.totalNodeCount_;
        this.initItem();
      }
      initItem(){
        for(let i=0;i<this.totalNodeCount;i++) {
          let textNode = typeNode.createNode(this.uiContext,'Text');
          textNode.initialize('this is '+i+' node');
          this.frameNodeList.push(textNode);
        }
      }
      onAttachToNode():void {
        if(this.onAttachToNodeFunc) {
          this.onAttachToNodeFunc()
        }
      }
      onGetChildId(index: number):number {
        return index;
      }
      onCreateChild(index: number): FrameNode {
        return this.frameNodeList[index];
      }
    
    }
    class TestController extends NodeController {
      nodeAdapterTest: NodeAdapterTest | undefined;
      rootNode:FrameNode|undefined ;
      makeNode(uiContext: UIContext): FrameNode | null {
        this.nodeAdapterTest =new NodeAdapterTest(uiContext)
        let rootNode = typeNode.createNode(uiContext, 'Column');
        rootNode.commonAttribute.width(200);
        rootNode.commonAttribute.height(200);
    
        // 适配后，onAttachToNode中使用的变量必须在attachNodeAdapter前赋值
        this.nodeAdapterTest.onAttachToNodeFunc = ()=>{
          hilog.info(0x0000, 'testTag', 'on attach to NodeAdapter');
        }
        NodeAdapter.attachNodeAdapter(this.nodeAdapterTest, rootNode);
       
        // 适配前，onAttachToNode中使用的变量可以在attachNodeAdapter后赋值
        this.nodeAdapterTest.onAttachToNodeFunc = ()=>{
           hilog.info(0x0000, 'testTag', 'on attach to NodeAdapter');
        }
       
        return rootNode;
      }
    }
    
    @Entry
    @Component
    struct Index {
      @State message: string = 'Hello World';
    
      build() {
        Row() {
          Column() {
            NodeContainer(new TestController())
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    
    ```

- OH_ArkUI_NodeAdapter_RegisterEventReceiver绑定方法触发时节点未上树

  在NDK开发中，如果通过[OH_ArkUI_NodeAdapter_RegisterEventReceiver](../../../application-dev/reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeadapter_registereventreceiver)注册了事件相关回调，并且回调事件枚举为NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE，该事件会在NodeAdapter绑定宿主节点后立即触发。由于此时节点可能尚未完全挂载，如果事件回调逻辑依赖宿主节点已挂载的状态（如访问布局信息或执行动画），需要将该部分逻辑迁移至宿主节点的onAppear回调中执行，具体示例如下。

    ```c
    #include <arkui/native_node.h>
    #include <arkui/native_interface.h>
    #include <stdio.h>
    #include <hilog/log.h>
    
    // 组件挂载时的回调函数
    static void OnAppear(ArkUI_NodeEvent* event) {
        OH_LOG_Print(LOG_APP, LOG_INFO, LOG_PRINT_DOMAIN, LOG_PRINT_TEXT, "Node is now attached to main tree");
    }
    
    // NodeAdapter事件监听器
    static void OnNodeAdapterEvent(ArkUI_NodeAdapterEvent* event, void* userData) {
        ArkUI_NodeAdapterEventType eventType = OH_ArkUI_NodeAdapterEvent_GetType(event);
        
        if (eventType == NODE_ADAPTER_EVENT_ON_ADD_NODE_TO_ADAPTER) {
            // 获取需要创建组件的索引位置
            uint32_t index = OH_ArkUI_NodeAdapterEvent_GetItemIndex(event);
            
            // 创建子组件
            ArkUINodeHandle childNode = OH_ArkUI_Node_Create("Text");
            
            // 获取NativeNodeAPI实例
            ArkUI_NativeNodeAPI_1* nativeNodeAPI = OH_ArkUI_GetNativeNodeAPI();
            
            // 设置子组件属性
            ArkUI_NumberValue widthValue[] = {{.f32 = 100.0f}};
            ArkUI_AttributeItem widthItem = {widthValue, 1, nullptr, nullptr};
            nativeNodeAPI->setAttribute(childNode, NODE_WIDTH, &widthItem);
            
            ArkUI_NumberValue heightValue[] = {{.f32 = 50.0f}};
            ArkUI_AttributeItem heightItem = {heightValue, 1, nullptr, nullptr};
            nativeNodeAPI->setAttribute(childNode, NODE_HEIGHT, &heightItem);
            
            // 将创建的组件返回给Adapter
            OH_ArkUI_NodeAdapterEvent_SetItem(event, childNode);
            
            // 为子组件注册onAppear事件
            nativeNodeAPI->registerNodeEvent(childNode, NODE_EVENT_ON_APPEAR, 0, NULL);
            nativeNodeAPI->addNodeEventReceiver(childNode, OnAppear);
        }
    }
    
    ArkUINodeHandle CreateRootNode(ArkUINodeAdapterHandle adapter) {
        // 1. 创建List容器节点
        ArkUINodeHandle listNode = OH_ArkUI_Node_Create("List");
        
        // 获取NativeNodeAPI实例
        ArkUI_NativeNodeAPI_1* nativeNodeAPI = OH_ArkUI_GetNativeNodeAPI();
        
        // 2. 设置List的基本属性
        ArkUI_NumberValue widthValue[] = {{.f32 = 200.0f}};
        ArkUI_AttributeItem widthItem = {widthValue, 1, nullptr, nullptr};
        nativeNodeAPI->setAttribute(listNode, NODE_WIDTH, &widthItem);
        
        ArkUI_NumberValue heightValue[] = {{.f32 = 200.0f}};
        ArkUI_AttributeItem heightItem = {heightValue, 1, nullptr, nullptr};
        nativeNodeAPI->setAttribute(listNode, NODE_HEIGHT, &heightItem);
        
        // 3. 设置NodeAdapter的总节点数量
        OH_ArkUI_NodeAdapter_SetTotalNodeCount(adapter, 100);
        
        // 4. 注册NodeAdapter事件监听器
        OH_ArkUI_NodeAdapter_RegisterEventReceiver(adapter, NULL, OnNodeAdapterEvent);
        
        // 5. 将NodeAdapter作为属性绑定到List节点
        // 不再使用OH_ArkUI_NodeAdapter_Attach，而是通过setAttribute设置
        ArkUI_AttributeItem adapterItem = {nullptr, 0, nullptr, adapter};
        nativeNodeAPI->setAttribute(listNode, NODE_LIST_NODE_ADAPTER, &adapterItem);
        
        return listNode;
    }
    
    ```

- OH_ArkUI_NodeAdapter_RegisterEventReceiver绑定方法在NodeAdapter绑定节点前设置

  开发者在NodeAdapter绑定宿主节点时，必须提前为NodeAdapter注册相关回调事件。如果OH_ArkUI_NodeAdapter_RegisterEventReceiver回调中包含NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE事件的处理逻辑，必须将这部分逻辑前移至绑定宿主节点前，以确保事件正常执行。

    ```c
    
    static void OnNodeAdapterEvent(ArkUINodeAdapterEvent* event, void* userData) {
        if (event->type == NODE_APPEAR_EVENT_WILL_ATTACH_TO_NODE) {
            // 处理添加节点事件
        }
    }
    
    void SetupAdapter(ArkUINodeAdapterHandle adapter, ArkUINodeHandle rootNode) {
         
        // 适配前，先绑定宿主节点再注册事件监听
        ArkUI_AttributeItem adapterItem = {nullptr, 0, nullptr, adapter};
        // 绑定宿主节点
        nativeNodeAPI->setAttribute(listNode, NODE_LIST_NODE_ADAPTER, &adapterItem);
        // 设置事件监听
        OH_ArkUI_NodeAdapter_RegisterEventReceiver(adapter, OnNodeAdapterEvent, NULL);
       
        // 适配后，先注册事件监听再绑定宿主节点
        // 设置事件监听
        OH_ArkUI_NodeAdapter_RegisterEventReceiver(adapter, OnNodeAdapterEvent, NULL);
        ArkUI_AttributeItem adapterItem = {nullptr, 0, nullptr, adapter};
        // 绑定宿主节点
        nativeNodeAPI->setAttribute(listNode, NODE_LIST_NODE_ADAPTER, &adapterItem);
    }
    ```