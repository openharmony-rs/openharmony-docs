# 自定义组件节点 (FrameNode)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

## 概述

对于拥有自定义前端的第三方框架（如JSON、XML、DOM树等），需将特定的DSL转换为ArkUI的声明式描述。如下图描述了JSON定义的前端框架和ArkUI声明式描述的对应关系。

![zh-cn_image_frame-node01](figures/frame-node01.png)

上述转换过程需要依赖额外的数据驱动，绑定至[Builder](../ui/state-management/arkts-builder.md)中，较为复杂且性能欠佳。这类框架通常依赖于ArkUI的布局、事件处理、基础的节点操作和自定义能力。大部分组件通过自定义实现，但需结合使用部分系统组件以实现混合显示，如下图示例既使用了FrameNode的自定义方法进行绘制，又使用了系统组件Column及其子组件Text，通过BuilderNode的方式将其挂载到根节点的FrameNode上混合显示。

![zh-cn_image_frame-node02](figures/frame-node02.png)

[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md)的设计初衷正是为了解决上述转换问题。FrameNode表示组件树中的实体节点，与自定义占位容器组件[NodeContainer](../reference/apis-arkui/arkui-ts/ts-basic-components-nodecontainer.md)相配合，实现在占位容器内构建一棵自定义的节点树。该节点树支持动态操作，如节点的增加、修改和删除。基础的FrameNode具备设置通用属性和事件回调的功能，同时提供完整的自定义能力，涵盖自定义测量、布局和绘制等方面。

除此之外，ArkUI还提供了获取和遍历系统组件对应代理FrameNode对象的能力（下文简称代理节点）。代理节点能够用于遍历整个UI的树形结构，支持获取系统组件节点的详细信息，以及额外注册组件的事件监听回调。

## 创建和删除节点

FrameNode提供了节点创建和删除的能力。可以通过FrameNode的构造函数创建自定义FrameNode节点，通过构造函数创建的节点对应一个实体的节点。同时，可以通过FrameNode中的[dispose](../reference/apis-arkui/js-apis-arkui-frameNode.md#dispose12)接口来实现与实体节点的绑定关系的解除。

> **说明：**
>
> - 在创建FrameNode对象的时候需要传入必选参数UIContext，若未传入UIContext对象或者传入不合法，则节点创建抛出异常。
>
> - 自定义占位组件将节点进行显示的时候需要保证UI上下文一致，否则会出现显示异常。
>
> - 若不持有FrameNode对象，则该对象会在GC的时候被回收。

## 判断节点是否可修改

[isModifiable](../reference/apis-arkui/js-apis-arkui-frameNode.md#ismodifiable12)用于查询当前节点类型是否为系统组件的代理节点。当FrameNode节点作为系统组件的代理节点的时候，该节点不可修改。即无法修改代理节点的自身属性以及其子节点的结构。

## 获取对应的RenderNode节点

FrameNode提供了[getRenderNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#getrendernode)接口，用于获取FrameNode中的RenderNode。可以通过对获取到的RenderNode对象进行操作，动态修改FrameNode上绘制相关的属性，具体可修改的属性参考[RenderNode](arkts-user-defined-arktsNode-renderNode.md)的接口。

> **说明：**
>
> - 无法获取系统组件代理FrameNode的RenderNode对象。
> 
> - BuilderNode中调用[getFrameNode](../reference/apis-arkui/js-apis-arkui-builderNode.md#getframenode)获取得到的FrameNode节点对象中，可以通过getRenderNode获取对应的根节点的RenderNode对象。

## 操作节点树

FrameNode提供了节点的增、删、查、改的能力，能够修改非代理节点的子树结构。可以对所有FrameNode的节点的父子节点做出查询操作，并返回查询结果。

> **说明：**
>
> 对节点进行增、删、改操作的时候，会对非法操作抛出异常信息。
>
> 通过查询获得的系统组件的代理节点，仅具备查询节点信息的作用，不具备修改节点属性的功能。代理节点不持有组件的实体节点，即不影响对应的节点的生命周期。
>
> 查询节点仅查询获得UI相关的节点，不返回语法节点。
>
> 使用自定义组件的场景下，可能查询获得自定义组件的新增节点，节点类型为“\_\_Common\_\_”。

<!-- [frameNodeTree_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeTree.ets) --> 

## 使用moveTo移动命令式节点

使用[moveTo](../reference/apis-arkui/js-apis-arkui-frameNode.md#moveto18)接口可以将FrameNode节点移动到新的父节点下，从而按需改变节点树结构。

> **说明：**
>
> 当前FrameNode如果不可修改，抛出异常信息。
>
> 目标父节点为[typeNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typenode12)时会校验子组件类型或个数，不满足抛出异常信息，限制情况请查看[typeNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typenode12)描述。
>
> 当前不支持对无组件类型的命令式节点进行移动。
>
> 当前仅支持以下类型的[TypedFrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typedframenode12)进行移动操作：[Stack](../reference/apis-arkui/js-apis-arkui-frameNode.md#stack12)、[XComponent](../reference/apis-arkui/js-apis-arkui-frameNode.md#xcomponent12)。对于其他类型的节点，移动操作不会生效。
>
> 当前仅支持根节点为以下类型组件的[BuilderNode](../reference/apis-arkui/js-apis-arkui-builderNode.md#buildernode-1)进行移动操作：[Stack](../reference/apis-arkui/arkui-ts/ts-container-stack.md)、[XComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)、[EmbeddedComponent](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md)。对于其他类型的组件，移动操作不会生效。

<!-- [frameNodeMoveTo_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeMoveTo.ets) --> 

![moveToDemo](figures/moveToDemo.gif)

## 设置节点通用属性和事件回调

FrameNode提供了[commonAttribute](../reference/apis-arkui/js-apis-arkui-frameNode.md#commonattribute12)和[commonEvent](../reference/apis-arkui/js-apis-arkui-frameNode.md#commonevent12)两个对象用于设置节点的[通用属性](../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)和[设置事件回调](../reference/apis-arkui/arkui-ts/ts-uicommonevent.md)。

> **说明：**
> 
> - 由于代理节点的属性不可修改，因此通过代理节点的commonAttribute修改节点的基础属性不生效。
> 
> - 设置的基础事件与系统组件定义的事件平行，参与事件竞争。设置的基础事件不覆盖系统组件事件。同时设置两个事件回调的时候，优先回调系统组件事件。

<!-- [frameNodeCommon_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeCommon.ets) --> 

## 自定义测量布局与绘制

通过重写[onDraw](../reference/apis-arkui/js-apis-arkui-frameNode.md#ondraw12)方法，可以自定义FrameNode的绘制内容。[invalidate](../reference/apis-arkui/js-apis-arkui-frameNode.md#invalidate12)接口可以主动触发节点的重新绘制。

通过重写[onMeasure](../reference/apis-arkui/js-apis-arkui-frameNode.md#onmeasure12)可以自定义FrameNode的测量方式，使用[measure](../reference/apis-arkui/js-apis-arkui-frameNode.md#measure12)可以主动传递布局约束触发重新测量。

通过重写[onLayout](../reference/apis-arkui/js-apis-arkui-frameNode.md#onlayout12)方法可以自定义FrameNode的布局方式，使用[layout](../reference/apis-arkui/js-apis-arkui-frameNode.md#layout12)方法可以主动传递位置信息并触发重新布局。

[setNeedsLayout](../reference/apis-arkui/js-apis-arkui-frameNode.md#setneedslayout12)可以将当前节点标记，在下一帧触发重新布局。

> **说明：**
> 
> - 对节点进行dispose解引用后，由于FrameNode对象不再对应一个实体节点，invalidate无法触发原有绑定节点的刷新。
> 
> - 通过onDraw方法进行的自定义绘制，绘制内容大小无法超出组件大小。

<!-- [frameNodeDraw_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeDraw.ets) --> 

## 查找节点及获取基础信息

FrameNode提供了查询接口用于返回实体节点的基础信息。具体返回的信息内容参考FrameNode中提供的接口。

查找获得FrameNode的方式包括三种：

1. 使用[getFrameNodeById](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getframenodebyid12)获取。

2. 使用[getFrameNodeByUniqueId](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getframenodebyuniqueid12)获取。

3. 通过[无感监听](../reference/apis-arkui/js-apis-arkui-observer.md)获取。

> **说明：**
>
> 1、当前接口提供的可查询的信息包括：
>
> - 节点大小：[getMeasuredSize](../reference/apis-arkui/js-apis-arkui-frameNode.md#getmeasuredsize12)，[getUserConfigSize](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigsize12)
> 
> - 布局信息：[getPositionToWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindow12)，[getPositionToParent](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparent12)，[getLayoutPosition](../reference/apis-arkui/js-apis-arkui-frameNode.md#getlayoutposition12)，[getUserConfigBorderWidth](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigborderwidth12)，[getUserConfigPadding](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigpadding12)，[getUserConfigMargin](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigmargin12)
> 
> - 节点信息：[getId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getid12)，[getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12)，[getNodeType](../reference/apis-arkui/js-apis-arkui-frameNode.md#getnodetype12)，[getOpacity](../reference/apis-arkui/js-apis-arkui-frameNode.md#getopacity12)，[isVisible](../reference/apis-arkui/js-apis-arkui-frameNode.md#isvisible12)，[isClipToFrame](../reference/apis-arkui/js-apis-arkui-frameNode.md#iscliptoframe12)，[isAttached](../reference/apis-arkui/js-apis-arkui-frameNode.md#isattached12)，[getInspectorInfo](../reference/apis-arkui/js-apis-arkui-frameNode.md#getinspectorinfo12)，[getCustomProperty](../reference/apis-arkui/js-apis-arkui-frameNode.md#getcustomproperty12)
>
> 2、无法获取UINode类型节点，例如：JsView节点、[Span](../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-span.md)、[ContainerSpan](../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-containerspan.md)、[ContentSlot](../../application-dev/reference/apis-arkui/arkui-ts/ts-components-contentSlot.md)、[ForEach](../../application-dev/reference/apis-arkui/arkui-ts/ts-rendering-control-foreach.md)、[LazyForEach](../../application-dev/reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md)、if/else组件等。

## 获取节点位置偏移信息

FrameNode提供了查询节点相对窗口、父组件以及屏幕位置偏移的信息接口（[getPositionToWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindow12)，[getPositionToParent](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparent12)，[getPositionToScreen](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoscreen12)，[getGlobalPositionOnDisplay](../reference/apis-arkui/js-apis-arkui-frameNode.md#getglobalpositionondisplay20)，[getPositionToWindowWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindowwithtransform12)，[getPositionToParentWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparentwithtransform12)，[getPositionToScreenWithTransform](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoscreenwithtransform12)，[getLayoutPosition](../reference/apis-arkui/js-apis-arkui-frameNode.md#getlayoutposition12)，[getUserConfigBorderWidth](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigborderwidth12)，[getUserConfigPadding](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigpadding12)，[getUserConfigMargin](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuserconfigmargin12)）。

[getPositionToWindow](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontowindow12)，[getPositionToParent](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoparent12)，[getPositionToScreen](../reference/apis-arkui/js-apis-arkui-frameNode.md#getpositiontoscreen12)三个接口获取到的位置信息关系如下图所示：

![FrameNode-Position-Relation](./figures/frameNode-position-relation.png)

<!-- [frameNodePosition_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodePosition.ets) --> 

## 通过typeNode创建具体类型的FrameNode节点

通过TypeNode创建具体类型的FrameNode节点，可以根据属性获取接口来检索用户设置的属性信息。

<!-- [frameNodeTypeNode_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeTypeNode.ets) --> 

## 解除当前FrameNode对象对实体FrameNode节点的引用关系

使用[dispose](../reference/apis-arkui/js-apis-arkui-frameNode.md#dispose12)接口可以立即解除当前FrameNode对象对实体FrameNode节点的引用关系。

> **说明：**
>
> 在调用dispose方法后，FrameNode对象不再对应任何实际的FrameNode节点。此时，若尝试调用以下查询接口：getMeasuredSize、getLayoutPosition、getUserConfigBorderWidth、getUserConfigPadding、getUserConfigMargin、getUserConfigSize，将导致应用程序触发jscrash。
>
> 通过[getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12)可以判断当前FrameNode是否对应一个实体FrameNode节点。当UniqueId大于0时表示该对象对应一个实体FrameNode节点。

<!-- [frameNodeDisposed_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeDisposed.ets) --> 

## 查询当前FrameNode是否解除引用

前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。

从API version 20开始，使用[isDisposed](../reference/apis-arkui/js-apis-arkui-frameNode.md#isdisposed20)接口查询当前FrameNode对象是否已解除与后端实体节点的引用关系，从而可以在操作节点前检查其有效性，避免潜在风险。

<!-- [frameNodeDisposed_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeIsDisposed.ets) --> 

## FrameNode的数据懒加载能力

提供[NodeAdapter](../reference/apis-arkui/js-apis-arkui-frameNode.md#nodeadapter12)对象替代ArkTS侧的LazyForEach功能，提供自定义节点的数据懒加载功能，实现按需迭代数据。

> **说明：**
>
> 入参不能为负数，入参为负数时不做处理。

<!-- [frameNodeLazyForEach_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeLazyForEach.ets) --> 

## 查询LazyForEach中的FrameNode节点信息

如果FrameNode子节点中包含[LazyForEach](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md)节点，[getChild](../reference/apis-arkui/js-apis-arkui-frameNode.md#getchild15)接口支持指定子节点展开模式[ExpandMode](../reference/apis-arkui/js-apis-arkui-frameNode.md#expandmode15)，以不同展开模式获取子节点。

当前支持如下子节点展开模式：

- ExpandMode.NOT_EXPAND：表示不展开当前FrameNode的子节点。如果FrameNode子节点中包含LazyForEach节点，获取在主节点树上的子节点时，不展开当前FrameNode的子节点。子节点序列号按在主节点树上的子节点计算。
- ExpandMode.EXPAND：表示展开当前FrameNode的子节点。如果FrameNode子节点中包含LazyForEach节点，获取任何子节点时，展开当前FrameNode的子节点。子节点序列号按所有子节点计算。
- ExpandMode.LAZY_EXPAND：表示按需展开当前FrameNode的子节点。如果FrameNode子节点中包含LazyForEach节点，获取在主节点树上的子节点时，不展开当前FrameNode的子节点；获取不在主节点树上的子节点时，展开当前FrameNode的子节点。子节点序列号按所有子节点计算。

可以使用[getFirstChildIndexWithoutExpand](../reference/apis-arkui/js-apis-arkui-frameNode.md#getfirstchildindexwithoutexpand15)和[getLastChildIndexWithoutExpand](../reference/apis-arkui/js-apis-arkui-frameNode.md#getlastchildindexwithoutexpand15)获取当前节点第一个和最后一个在主节点树上的子节点的序列号，其中子节点序列号按所有子节点计算。

<!-- [frameNodeLazyForEachSelect_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeLazyForEachSelect.ets) --> 

## 调整自定义绘制Canvas的变换矩阵

从API version 12开始，通过重写FrameNode的[onDraw](../reference/apis-arkui/js-apis-arkui-frameNode.md#ondraw12)方法，可以重写默认绘制方法。

通过[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)可以调整自定义绘制画布的变换矩阵。

> **说明：**
> 
> - [getTotalMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#gettotalmatrix12)获取的是用来记录绘制指令的临时canvas的变换矩阵。
> 
> - 如果开发者希望对画布进行预期的变换，应使用[concatMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#concatmatrix12)而不是[setMatrix](../../application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#setmatrix12)，因为setMatrix会覆盖原本真实canvas上存在的变换矩阵。

**ArkTS接口调用示例：**

<!-- [frameNodeCanvas_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/FrameNode/entry/src/main/ets/pages/framenode/FrameNodeCanvas.ets) --> 

![FrameNode-canvas](./figures/frameNode-canvas.png)
