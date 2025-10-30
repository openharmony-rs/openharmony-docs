# 使用列表

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong-->
<!--Designer: @yylong-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

ArkUI开发框架在NDK接口提供了列表组件，使用列表可以轻松高效地显示结构化、可滚动的信息。列表组件支持控制滚动位置、支持分组显示内容、支持使用NodeAdapter实现懒加载以提升列表创建性能。

## 创建列表

参考[接入ArkTS页面章节](../ui/ndk-access-the-arkts-page.md)实现列表创建。 

## 监听滚动事件 

参考[监听组件事件](ndk-listen-to-component-events.md)章节实现列表滚动事件监听。 

## 使用懒加载 

### NodeAdapter介绍 

NDK提供了[NodeAdapter](../reference/apis-arkui/capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象替代ArkTS侧的LazyForEach功能，用于按需生成子组件，NodeAdapter支持在List/ListItemGroup、Grid、WaterFlow、Swiper组件中使用。

- 设置了NodeAdapter属性的节点，不再支持addChild等直接添加子组件的接口。子组件完全由NodeAdapter管理，使用属性方法设置NodeAdapter时，会判断父组件是否已经存在子节点，如果父组件已经存在子节点，则设置NodeAdapter操作失败，返回错误码。

- NodeAdapter通过相关事件通知开发者按需生成组件，类似组件事件机制，开发者使用NodeAdapter时要注册[事件监听器](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_nodeadapter_registereventreceiver)，在监听器事件中处理逻辑，相关事件通过[ArkUI_NodeAdapterEventType](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeadaptereventtype)定义。另外NodeAdapter不会主动释放不在屏幕内显示的组件对象，开发者需要在[NODE_ADAPTER_EVENT_ON_REMOVE_NODE_FROM_ADAPTER](../reference/apis-arkui/capi-native-node-h.md#arkui_nodeadaptereventtype)事件中进行组件对象的释放，或者进行缓存复用。下图展示了典型列表滑动场景下的事件触发机制：
  ![zh-cn_image_0000001949769409](figures/zh-cn_image_0000001949769409.png)


### 实现懒加载适配器

使用ArkUIListItemAdapter类来管理懒加载适配器，在类的构造中创建NodeAdapter对象，并给NodeAdapter对象设置事件监听器，在类的析构函数中，销毁NodeAdapter对象。

<!-- @[Lazy_loading_of_text_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListItemAdapter.h) -->

### 在列表中应用懒加载适配器 

1. 在ArkUIListNode中添加SetLazyAdapter函数，给列表节点设置NODE_LIST_NODE_ADAPTER属性，并将NodeAdapter作为属性入参传入。
   <!-- @[List_encapsulated_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListNode.h) -->

2. 创建List使用懒加载的示例代码，调用List节点的SetLazyAdapter接口设置懒加载适配器。
   <!-- @[Grouped_List_Interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/LazyTextListExample1.h) -->

3. 在NativeEntry.cpp中调用List使用懒加载的示例代码。
   <!-- @[Interface_entrance_mounting_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/NativeEntry.cpp) -->
## 控制列表滚动位置

1. 控制列表滚动到指定偏移量位置。
   <!-- @[ScrollTo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListNode.h) -->
2. 控制列表滚动到指定元素。 
   <!-- @[ScrollToIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListNode.h) -->

3. 控制列表滚动指定偏移量。
   <!-- @[ScrollBy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListNode.h) -->
## ListItem横划删除 

1. ListItem设置NODE_LIST_ITEM_SWIPE_ACTION属性，将ArkUI_ListItemSwipeActionOption对象作为属性参数传入。
   <!-- @[Provide_wrapper_class_list_items](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListItemNode.h) -->

2. 创建ListItem时，创建ListItem的划出组件，并绑定点击事件，在点击事件中执行删除数据源操作。ListItem复用时，更新划出组件的绑定事件。
   <!-- @[Item_adapter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListItemAdapter.h) -->
3. ArkUIListItemAdapter中新增RemoveItem，用于删除数据源并且调用OH_ArkUI_NodeAdapter_RemoveItem接口通知框架刷新UI。
   <!-- @[Remove_Item](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListItemAdapter.h) -->
## 使用分组列表 
1. 分组列表使用ListItemGroup组件实现，ListItemGroup支持添加header、footer设置函数，支持使用懒加载。
   <!-- @[Use_grouped_lists](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListItemGroupNode.h) -->
2. List组件设置吸顶。
   <!-- @[SetSticky](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/ArkUIListNode.h) -->
3. List组件下使用ListItemGroup实现分组列表界面。
   <!-- @[Grouped_List](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NativeType/NdkCreateList/entry/src/main/cpp/LazyTextListExample.h) -->

