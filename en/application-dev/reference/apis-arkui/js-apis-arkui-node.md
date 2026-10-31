# @ohos.arkui.node (Custom Node)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d89c4be0c26be57dcac6e3a0bb8b7f968642aa19 translatedAt=2026-07-29T09:29:59.902Z pushedAt=2026-07-31T03:48:19.848Z -->

The **Node** module provides level-2 module APIs of custom nodes to export and use. Custom nodes allow you to flexibly create, mount, and manage component tree nodes, and are used in scenarios where UI components need to be dynamically built, reused, and extended.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - Custom nodes are not available in DevEco Studio Previewer.

## BuilderNode

The [BuilderNode](./js-apis-arkui-builderNode.md) module provides APIs for creating a BuilderNode – a custom node that can be used to mount built-in components. It is used in scenarios where system components need to be embedded and reused in custom nodes. Avoid mounting a BuilderNode as a child node to other custom nodes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## FrameNode

The [FrameNode](./js-apis-arkui-frameNode.md) module provides APIs for a FrameNode, which represents an entity node in the component tree. It is used in scenarios where entity nodes in component trees need to be directly operated and managed. A [NodeController](./js-apis-arkui-nodeController.md) can be mounted to [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) through the FrameNode held by a [BuilderNode](./js-apis-arkui-builderNode.md), and a [RenderNode](./js-apis-arkui-renderNode.md) can be obtained through the FrameNode and mounted to another FrameNode.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## NodeController

The [NodeController](./js-apis-arkui-nodeController.md) module provides APIs for managing custom nodes, such as creating, showing, and updating custom nodes, and APIs for mounting custom nodes to a [NodeContainer](arkui-ts/ts-basic-components-nodecontainer.md) component. It is used in scenarios where the lifecycle and display states of custom nodes need to be dynamically managed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Graphics

The [Graphics](./js-apis-arkui-graphics.md) module provides APIs for defining attributes of a custom node, including the graphical appearance and rendering. It is used in scenarios where fine-grained control over node rendering effects is required.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## RenderNode

The [RenderNode](./js-apis-arkui-renderNode.md) module provides APIs for creating a RenderNode in custom drawing settings. It is used in scenarios where graphical content (such as custom charts, game graphics, and hand-drawn animations) needs to be self-drawn.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## XComponentNode

The [XComponentNode](./js-apis-arkui-xcomponentNode.md) module provides APIs for a XComponentNode, which represents an **XComponent** component in a component tree. You can write EGL/OpenGL ES and media data and display it on the XComponent, whose rendering type can be dynamically modified. It is used in scenarios where graphics rendering or media data processing needs to be embedded in custom nodes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Obtaining UI Context

1. Call [getUIContext()](arkts-apis-window-Window.md#getuicontext10) in **ohos.window** to obtain the **UIContext** instance.

2. Call the built-in method [getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext) of the custom component to obtain the **UIContext** instance.

3. Use the input parameter of the [makeNode](./js-apis-arkui-nodeController.md#makenode) callback of [NodeController](./js-apis-arkui-nodeController.md) to obtain the **UIContext** instance.