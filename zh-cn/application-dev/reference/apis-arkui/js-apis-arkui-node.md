# @ohos.arkui.node 

Node将自定义节点的二级模块API组织在一起，方便开发者进行导出使用。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 当前不支持在预览器中使用自定义节点。

## BuilderNode

[BuilderNode](./js-apis-arkui-builderNode.md)模块提供能够挂载系统组件的自定义节点BuilderNode。不建议将BuilderNode作为子节点挂载到其他自定义节点上。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FrameNode

[FrameNode](./js-apis-arkui-frameNode.md)模块提供自定义节点FrameNode，表示组件树的实体节点。[NodeController](./js-apis-arkui-nodeController.md)可通过[BuilderNode](./js-apis-arkui-builderNode.md)持有的FrameNode将其挂载到[NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md)上，也可通过FrameNode获取[RenderNode](./js-apis-arkui-renderNode.md)，挂载到其他FrameNode上。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NodeController

[NodeController](./js-apis-arkui-nodeController.md)模块提供NodeController，用于实现自定义节点的创建、显示、更新等操作，并负责将自定义节点挂载到[NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md)上。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Graphics

[Graphics](./js-apis-arkui-graphics.md)模块：提供自定义节点相关属性设置的定义。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RenderNode

[RenderNode](./js-apis-arkui-renderNode.md)模块提供自绘制渲染节点RenderNode，支持开发者通过C API进行开发，完成自定义绘制需求。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## XComponentNode

[XComponentNode](./js-apis-arkui-xcomponentNode.md)模块提供XComponent节点XComponentNode，表示组件树中的XComponent组件，用于EGL/OpenGLES和媒体数据写入，并支持动态修改节点渲染类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full



## UIContext获取方法
1.使用ohos.window中的[getUIContext()](arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例。

2.可以通过自定义组件内置方法[getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext)获取。

3.可以在[NodeController](./js-apis-arkui-nodeController.md)的[makeNode](./js-apis-arkui-nodeController.md#makenode)回调方法中获取。

