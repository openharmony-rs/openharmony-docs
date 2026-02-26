# FrameNode支持多线程创建组件 (ArkTS-Sta)

## 概述

在API version 24之前，FrameNode组件的创建与初始化必须在应用程序的主线程中执行。这导致开发者在集成时，需要将任务切换回主线程，不仅增加了调用代码的复杂度，也限制了组件构造过程的灵活性与性能。

随着用户界面的日益复杂，页面中可能同时存在大量动态生成的UI组件，这类任务堆积在单一主线程中执行，往往导致启动缓慢、动画掉帧及界面卡顿，直接影响用户体验。

针对这些问题，在API version 24中，ArkUI引入了FrameNode的多线程支持能力，为开发者带来了以下提升：

- **性能与体验显著优化：** 多线程能力支持组件创建与初始化任务并行执行，充分利用设备多核CPU，减少页面启动与界面构造阶段的总体耗时。主线程专注于动画渲染与用户输入，确保界面流畅与交互及时。

- **为后续功能扩展提供更好的灵活性：** 多线程支持不仅解决当前性能瓶颈，还为未来引入复杂、高负载的界面组件提供扩展空间，帮助开发者在设计时拥有更大灵活度与掌控力，为持续提升用户体验创造条件。

通过此次优化，开发者可专注于自身逻辑实现，无需关注并发与线程切换等底层细节。在更大任务量与复杂场景下，开发者将获得更可预测、高性能的界面创建体验。

> **说明：**
>
> 本文档主要介绍如何通过FrameNode相关接口在多线程中创建UI组件并设置属性和事件注册。关于如何在ArkTS-Sta中进行多线程编程的具体介绍（包括 EAWorker 的使用、线程管理、任务调度等），请参考 [EAWorker（独占线程任务执行器）](../reference/native-lib/eaworker_managed.md)。

## 使用方式

使用[FrameNodeOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#framenodeoptions24)接口配置FrameNode创建时的选项，可设置FrameNode是否支持多线程操作。

### 创建支持多线程的FrameNode

- 使用构造函数创建支持多线程的FrameNode。

  ```ts
  import { FrameNode, UIContext } from '@kit.ArkUI';
  
  const uiContext = this.getUIContext();
  const frameNode = new FrameNode(uiContext, { supportMultiThread: true });
  ```

- 使用typeNode创建支持多线程的指定类型FrameNode。

  ```ts
  import { typeNode, UIContext } from '@kit.ArkUI';
  
  const uiContext = this.getUIContext();
  const columnNode = typeNode.createColumnNode(uiContext, { supportMultiThread: true });
  const rowNode = typeNode.createRowNode(uiContext, { supportMultiThread: true });
  const stackNode = typeNode.createStackNode(uiContext, { supportMultiThread: true });
  ```

### 支持多线程创建的组件类型

以下组件类型支持通过FrameNodeOptions配置多线程创建。

- 布局容器：[Column](../reference/apis-arkui/arkui-ts/ts-container-column.md)、[Row](../reference/apis-arkui/arkui-ts/ts-container-row.md)、[Stack](../reference/apis-arkui/arkui-ts/ts-container-folderstack.md)、[Flex](../reference/apis-arkui/arkui-ts/ts-container-flex.md)、[RelativeContainer](../reference/apis-arkui/arkui-ts/ts-container-relativecontainer.md)。
- 滚动容器：[List](../reference/apis-arkui/arkui-ts/ts-container-arclist.md)、[ListItem](../reference/apis-arkui/arkui-ts/ts-container-listitem.md)、[ListItemGroup](../reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md)、[Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md)、[Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)、[GridItem](../reference/apis-arkui/arkui-ts/ts-container-griditem.md)、[WaterFlow](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)、[FlowItem](../reference/apis-arkui/arkui-ts/ts-container-flowitem.md)、[Swiper](../reference/apis-arkui/arkui-ts/ts-container-arcswiper.md)。
- 基础组件：[Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、[Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md)、[Progress](../reference/apis-arkui/arkui-ts/ts-basic-components-progress.md)、[LoadingProgress](../reference/apis-arkui/arkui-ts/ts-basic-components-loadingprogress.md)。
- 输入组件：[TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)、[TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)。
- 按钮组件：[Button](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md)、[Checkbox](../reference/apis-arkui/arkui-ts/ts-basic-components-checkbox.md)、[CheckboxGroup](../reference/apis-arkui/arkui-ts/ts-basic-components-checkboxgroup.md)、[Radio](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md)、[Slider](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md)、[Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md)。
- 其他组件：[XComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)。

## 调用规范与线程安全

- 多线程接口规范请参考[多线程FrameNode接口集规格](#多线程FrameNode接口集规格)。调用接口时建议捕获异常，如果在非UI线程中调用不支持的接口，将抛出异常。

- 虽然ArkUI提供了线程安全的组件创建与属性设置接口，但是，单个组件内部仍非线程安全。请避免在多个线程中同时操作同一组件或同一组件树，否则可能产生不可预测的结果。

- 多线程接口中，组件有以下两种状态：

  - **Free（游离状态）：** 组件未挂载到主树，不参与UI流水线，属性可安全更新。
  - **Attached（已挂载状态）：** 组件已挂载，交由UI流水线管理，属性更新必须在UI线程中调用，否则抛出异常。

- 多线程场景下，共有以下两种场景会导致接口抛出异常：

  - 在非UI线程中调用不支持多线程的接口将抛出异常。
  - 挂载到UI主树后，非UI线程调用组件接口将抛出异常。

- 建议开发者使用try-catch捕获异常及时进行异常处理以确保代码的健壮性。

## 多线程FrameNode接口集规格

下面介绍FrameNode接口集中各个接口的多线程规格，接口包括：[组件创建销毁](#组件创建销毁)，[组件树操作](#组件树操作)，[组件属性查询](#组件属性查询)，[组件布局测算](#组件布局测算)，[组件样式查询](#组件样式查询)，[组件动画](#组件动画)，[组件事件](#组件事件)，[组件生命周期](#组件生命周期)，[组件跨语言](#组件跨语言)，[坐标转换](#坐标转换)和[其他接口](#其他接口)。

### 组件创建销毁

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- |  
| [constructor](../reference/apis-arkui/js-apis-arkui-frameNode.md#constructor23) | 创建FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createColumnNode | 创建Column类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createRowNode | 创建Row类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createStackNode | 创建Stack类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createFlexNode | 创建Flex类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createRelativeContainerNode | 创建RelativeContainer类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createLoadingProgressNode | 创建LoadingProgress类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createImageNode | 创建Image类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createListNode | 创建List类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createListItemNode | 创建ListItem类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createListItemGroupNode | 创建ListItemGroup类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createProgressNode | 创建Progress类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createScrollNode | 创建Scroll类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createGridNode | 创建Grid类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createGridItemNode | 创建GridItem类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createWaterFlowNode | 创建WaterFlow类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createFlowItemNode | 创建FlowItem类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createTextNode | 创建Text类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createTextInputNode | 创建TextInput类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createTextAreaNode | 创建TextArea类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| typeNode.createSwiperNode | 创建Swiper类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createXComponentNodeDefault](../reference/apis-arkui/js-apis-arkui-frameNode.md#createxcomponentnodedefault23) | 创建XComponent类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createXComponentNodeWithOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#createxcomponentnodewithoptions23) | 创建XComponent类型的FrameNode（带选项）。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createButtonNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createbuttonnode23) | 创建Button类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createCheckboxNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createcheckboxnode23) | 创建Checkbox类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createCheckboxGroupNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createcheckboxgroupnode23) | 创建CheckboxGroup类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createRadioNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createradionode23) | 创建Radio类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createSliderNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createslidernode23) | 创建Slider类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [typeNode.createToggleNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#createtogglenode23) | 创建Toggle类型的FrameNode。 | 支持 | 支持在任意线程调用。 |
| [disposeNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#dispose12) | 销毁节点指针指向的节点对象。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |

### 组件树操作

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [appendChild](../reference/apis-arkui/js-apis-arkui-frameNode.md#appendchild12) | 将child节点挂载到parent节点的子节点列表中。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [insertChildAfter](../reference/apis-arkui/js-apis-arkui-frameNode.md#insertchildafter12) | 将child节点挂载到parent节点的子节点列表中，挂载位置在sibling节点之后。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [removeChild](../reference/apis-arkui/js-apis-arkui-frameNode.md#removechild12) | 将child节点从parent节点的子节点列表中移除。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [clearChildren](../reference/apis-arkui/js-apis-arkui-frameNode.md#clearchildren12) | 移除node节点的所有子节点。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getChild](../reference/apis-arkui/js-apis-arkui-frameNode.md#getchild12) | 获取node节点的子节点指针，位置由position指定。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getFirstChild](../reference/apis-arkui/js-apis-arkui-frameNode.md#getfirstchild12) | 获取node节点的第一个子节点指针。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getNextSibling](../reference/apis-arkui/js-apis-arkui-frameNode.md#getnextsibling12) | 获取node节点的下一个兄弟节点指针。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getPreviousSibling](../reference/apis-arkui/js-apis-arkui-frameNode.md#getprevioussibling12) | 获取node节点的上一个兄弟节点指针。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getParent](../reference/apis-arkui/js-apis-arkui-frameNode.md#getparent12) | 获取node节点的父节点。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getChildrenCount](../reference/apis-arkui/js-apis-arkui-frameNode.md#getchildrencount12) | 获取node节点的子节点个数。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| adoptChild | 收养子节点。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| removeAdoptedChild | 移除收养的子节点。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [moveTo](../reference/apis-arkui/js-apis-arkui-frameNode.md#moveto18) | 移动节点到指定位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件属性查询

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [getId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getid12) | 获取节点ID。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12) | 获取唯一ID。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getNodeType](../reference/apis-arkui/js-apis-arkui-frameNode.md#getnodetype12) | 获取节点类型。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getOpacity](../reference/apis-arkui/js-apis-arkui-frameNode.md#getopacity12) | 获取透明度。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [isVisible](../reference/apis-arkui/js-apis-arkui-frameNode.md#isvisible12) | 获取可见性。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [isClipToFrame](../reference/apis-arkui/js-apis-arkui-frameNode.md#iscliptoframe12) | 获取裁剪状态。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [isAttached](../reference/apis-arkui/js-apis-arkui-frameNode.md#isattached12) | 获取是否已挂载。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| isOnMainTree | 获取是否在主树上。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| isOnRenderTree | 获取是否在渲染树上。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件布局测算

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [getMeasuredSize](../reference/apis-arkui/js-apis-arkui-frameNode.md#getmeasuredsize12) | 获取测算完成后的宽高尺寸。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getLayoutPosition](../reference/apis-arkui/js-apis-arkui-frameNode.md#getlayoutposition12) | 获取布局完成后的位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [setMeasuredSize](../reference/apis-arkui/js-apis-arkui-frameNode.md#setmeasuredsize12) | 在测算回调函数中设置组件测算完成后的宽和高。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [setLayoutPosition](../reference/apis-arkui/js-apis-arkui-frameNode.md#setlayoutposition12) | 在布局回调函数中设置组件的位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [measure](../reference/apis-arkui/js-apis-arkui-frameNode.md#measure12) | 对node节点进行测算，可以通过getMeasuredSize获取测算后的大小。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [layout](../reference/apis-arkui/js-apis-arkui-frameNode.md#layout12) | 对node节点进行布局并传递该组件相对父组件的期望位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [setNeedsLayout](../reference/apis-arkui/js-apis-arkui-frameNode.md#setneedslayout12) | 标记节点需要布局。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindow12) | 获取相对窗口位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToParent](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparent12) | 获取相对父节点位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToScreen](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoscreen12) | 获取相对屏幕位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getGlobalPositionOnDisplay](../reference/apis-arkui/js-apis-arkui-frameNode.md#getglobalpositionondisplay20) | 获取显示位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToWindowWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindowwithtransform12) | 获取相对窗口位置（含变换）。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToParentWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparentwithtransform12) | 获取相对父节点位置（含变换）。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getPositionToScreenWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoscreenwithtransform12) | 获取相对屏幕位置（含变换）。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件样式查询

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [getUserConfigBorderWidth](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigborderwidth12) | 获取边框宽度。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getUserConfigPadding](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigpadding12) | 获取内边距。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getUserConfigMargin](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigmargin12) | 获取外边距。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getUserConfigSize](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigsize12) | 获取尺寸。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件动画

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [createAnimation](../reference/apis-arkui/js-apis-arkui-frameNode.md#createanimation20) | 创建动画。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [cancelAnimations](../reference/apis-arkui/js-apis-arkui-frameNode.md#cancelanimations20) | 取消动画。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getNodePropertyValue](../reference/apis-arkui/js-apis-arkui-frameNode.md#getnodepropertyvalue20) | 获取节点属性值。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件事件

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| getCommonEvent | 获取公共事件。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getInteractionEventBindingInfo](../reference/apis-arkui/js-apis-arkui-frameNode.md#getinteractioneventbindinginfo19) | 获取交互事件绑定信息。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [addSupportedUIStates](../reference/apis-arkui/js-apis-arkui-frameNode.md#addsupporteduistates20) | 添加支持的UI状态。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [removeSupportedUIStates](../reference/apis-arkui/js-apis-arkui-frameNode.md#removesupporteduistates20) | 移除支持的UI状态。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件生命周期

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [invalidate](../reference/apis-arkui/js-apis-arkui-frameNode.md#invalidate12) | 使节点失效。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [disposeTree](../reference/apis-arkui/js-apis-arkui-frameNode.md#disposetree12) | 销毁节点树。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [reuse](../reference/apis-arkui/js-apis-arkui-frameNode.md#reuse18) | 复用节点。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [recycle](../reference/apis-arkui/js-apis-arkui-frameNode.md#recycle18) | 回收节点。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| applyAttributesFinish | 应用属性完成。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 组件跨语言

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [setCrossLanguageOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#setcrosslanguageoptions15) | 设置跨语言选项。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getCrossLanguageOptions](../reference/apis-arkui/js-apis-arkui-frameNode.md#getcrosslanguageoptions15) | 获取跨语言选项。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 坐标转换

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [convertPositionToWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#convertpositiontowindow23) | 转换位置到窗口坐标。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [convertPositionFromWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#convertpositionfromwindow23) | 从窗口坐标转换位置。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |

### 其他接口

| 接口名 | 描述 | 非UI线程调用 | 多线程规格 |
| -------- | ------- | ------- | ------- | 
| [getInspectorInfo](../reference/apis-arkui/js-apis-arkui-frameNode.md#getinspectorinfo12) | 获取检查器信息。 | 不支持 | 只支持UI线程调用，否则接口抛出异常。 |
| [getFirstChildIndexWithoutExpand](../reference/apis-arkui/js-apis-arkui-frameNode.md#getfirstchildindexwithoutexpand15) | 获取第一个子节点索引（不展开）。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |
| [getLastChildIndexWithoutExpand](../reference/apis-arkui/js-apis-arkui-frameNode.md#getlastchildindexwithoutexpand15) | 获取最后一个子节点索引（不展开）。 | 支持 | 在非UI线程调用函数操作已挂载到UI树上的节点时，接口抛出异常。 |

## 示例

从API version 24开始，FrameNode引入了多线程支持能力。

如下示例展示了如何使用FrameNode在多线程中并行创建UI组件。

```ts
import { NodeContainer, Entry, Component, Column, Button, Text, Flex, Row, Color, UIContext, ClickEvent, FontWeight } from '@ohos.arkui.component';
import { FrameNode, typeNode, NodeController } from '@ohos.arkui.node';
import { State } from '@ohos.arkui.stateManagement';

class MultiThreadNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private isCreated: boolean = false;

  constructor() {
    super();
  }

  makeNode(uiContext: UIContext): FrameNode | null {
    if (!this.rootNode) {
      this.uiContext = uiContext;
      this.rootNode = typeNode.createColumnNode(uiContext, { supportMultiThread: true });
      this.rootNode!.commonAttribute.width('100%').height('100%');
      this.createNodeOnUIThread();
      this.createNodeOnUserThread();
      this.isCreated = true;
    }
    return this.rootNode;
  }

  // 在UI线程中创建组件树
  createNodeOnUIThread(): void {
    const UI_NODE_TREE_NUMBER = 2;

    for (let i = 0; i < UI_NODE_TREE_NUMBER; i++) {
      const nodeTree = this.createNodeTree(false);
      this.rootNode!.appendChild(nodeTree);
    }
  }

  // 在用户线程中创建组件树
  createNodeOnUserThread(): void {
    const USER_NODE_TREE_NUMBER = 3;
    const userWorker = new EAWorker();
    userWorker.start();

    for (let i = 0; i < USER_NODE_TREE_NUMBER; i++) {
      userWorker.postTask(() => {
        try {
          const nodeTree = this.createNodeTree(true);
          const mainWorker = EAWorker.main();
          if (mainWorker) {
            mainWorker.postTask(() => {
              this.rootNode!.appendChild(nodeTree);
            });
          }
        } catch (error) {
          console.error(`createNodeOnUserThread error: ${JSON.stringify(error)}`);
        }
      });
    }
    userWorker.quit();
  }

  // 创建节点树
  createNodeTree(isOnUserThread: boolean): FrameNode {
    const columnNode = typeNode.createColumnNode(this.uiContext!, { supportMultiThread: true });
    columnNode.commonAttribute.width('80%').height(70)

    const rowNode = typeNode.createRowNode(this.uiContext!, { supportMultiThread: true });
    rowNode.commonAttribute.width('100%').height('100%');

    const buttonNode1 = typeNode.createButtonNode(this.uiContext!, { supportMultiThread: true });
    buttonNode1.commonAttribute.width(150).height(50).margin(5);
    buttonNode1.commonEvent.setOnClick((event: ClickEvent) => {
      console.info(`${isOnUserThread ? 'OnUserThread' : 'OnUIThread'} button clicked`);
    });
    const textNode1 = typeNode.createTextNode(this.uiContext!, { supportMultiThread: true });
    textNode1.initialize(`${isOnUserThread ? 'OnUserThread' : 'OnUIThread'}`)
      .fontColor(isOnUserThread ? Color.White : Color.Black);
    buttonNode1.appendChild(textNode1);

    const buttonNode2 = typeNode.createButtonNode(this.uiContext!, { supportMultiThread: true });
    buttonNode2.commonAttribute.width(150).height(50).margin(5);
    buttonNode2.commonEvent.setOnClick((event: ClickEvent) => {
      console.info(`${isOnUserThread ? 'OnUserThread' : 'OnUIThread'} button clicked`);
    });
    const textNode2 = typeNode.createTextNode(this.uiContext!, { supportMultiThread: true });
    textNode2.initialize(`${isOnUserThread ? 'OnUserThread' : 'OnUIThread'}`)
      .fontColor(isOnUserThread ? Color.White : Color.Black);
    buttonNode2.appendChild(textNode2);

    rowNode.appendChild(buttonNode1);
    rowNode.appendChild(buttonNode2);
    columnNode.appendChild(rowNode);

    return columnNode;
  }
}

@Entry
@Component
struct Index {
  @State isShow: boolean = false;
  @State message: string = 'CreateNodeTree';
  private multiThreadNodeController: MultiThreadNodeController = new MultiThreadNodeController();

  build() {
    Flex() {
      Column(undefined) {
        Text('FrameNode支持多线程创建组件')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
        Button(this.message)
          .onClick(() => {
            this.isShow = !this.isShow;
            if (this.isShow) {
              this.message = 'DisposeNodeTree';
            } else {
              this.message = 'CreateNodeTree';
            }
          })
        if (this.isShow) {
          NodeContainer(this.multiThreadNodeController)
        }
      }.width('100%')
    }.width('100%')
  }
}
```

![build_on_multi_thread](figures/framenode_build_on_multi_thread.gif)
