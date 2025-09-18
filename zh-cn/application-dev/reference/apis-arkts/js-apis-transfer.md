# @ohos.transfer (系统对象转换工具)

ArkTS1.1和ArkTS1.2交互过程中，存在系统对象的交互。本模块提供了系统对象转换能力：

- 从ArkTS1.2系统对象转换为ArkTS1.1系统对象的能力。

- 从ArkTS1.1系统对象转换为ArkTS1.2系统对象的能力。

> **说明：**
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块仅使用于ArkTS1.2。
>
> - 本模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

## 导入模块

```ts
import { transfer } from '@kit.ArkTS'
```

## transfer.transferStatic

transferStatic(input: Any, inputName: string): Object

从ArkTS1.1系统对象转换为ArkTS1.2系统对象。

**原子化服务API**：从API version 20 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 名称 | 类型   | 必填 | 说明                             |
| ---- | ------ | ---- | -------------------------------- |
| input | Any | 是   | 待转换的ArkTS1.1对象。 |
| inputName | string | 是   | 转换对象的key值，取值参见[key值列表](#转换对象key值列表)。 |

**返回值：**

| 类型                    | 说明                             |
| ----------------------- | -------------------------------- |
| Object | 转换后的ArkTS1.2对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 10200067 | Transfer Error. The input name is not supported! |

**示例：**

```ts
// ArkTS1.1环境
import { dyamic2Static } from 'har2';
let dynamic_obj = new ArrayBuffer(8);
dyamic2Static(dynamic_obj); // 调用ArkTS1.2环境中的dyamic2Static方法

// ArkTS1.2环境
import { transfer } from '@kit.ArkTS'
function dyamic2Static(dynamic_obj: Any) {
   let static_obj = transfer.transferStatic(dynamic_obj, 'InteropTransferHelper')
   // handle static_obj
}
```

## transfer.transferDynamic

transferDynamic(input: Object, inputName: string): Any

从ArkTS1.2系统对象转换为ArkTS1.1系统对象。

**原子化服务API**：从API version 20 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 名称 | 类型   | 必填 | 说明                             |
| ---- | ------ | ---- | -------------------------------- |
| input | Object | 是   | 待转换的ArkTS1.2对象。 |
| inputName | string | 是   | 转换对象的key值，取值参见[key值列表](#转换对象key值列表)。 |

**返回值：**

| 类型                    | 说明                             |
| ----------------------- | -------------------------------- |
| Any | 转换后的ArkTS1.1对象。 |

**错误码：**

以下错误码的详细介绍请参见[语言基础类库错误码](errorcode-utils.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 10200067 | Transfer Error. The input name is not supported! |

**示例：**

```ts
// ArkTS1.2环境
import { transfer } from '@kit.ArkTS'

let static_obj = new ArrayBuffer(8);
let dynamic_obj = transfer.transferDynamic(static_obj, 'InteropTransferHelper')
// 调用1.0中的har1func方法处理dynamic_obj
let moduleName = ESValue.load('@nomalized:....');
let har1func = moduleName.getProperty('har1func');
har1func.invoke(ESObject.wrap(dynamic_obj));


// ArkTS1.1环境
export function har1func(dynamic_obj: Any) {
    // handle dynamic_obj
}
```

## 转换对象key值列表
| key  |系统对象 |
|------ | ----  |
|"InteropTransferHelper" | [ArrayBuffer](../../arkts-utils/arraybuffer-object.md)|
| "ArkUI.NavDestinationInfo" | [uiObserver.NavDestinationInfo](../apis-arkui/js-apis-arkui-observer.md#navdestinationinfo)|
| "ArkUI.NavigationInfo" | [uiObserver.NavigationInfo](../apis-arkui/js-apis-arkui-observer.md#navigationinfo12)|
| "ArkUI.RouterPageInfo" | [uiObserver.RouterPageInfo](../apis-arkui/js-apis-arkui-observer.md#routerpageinfo)|
| "AbilityKit.UIAbilityContext" | [common.UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#uiabilitycontext)|
| "ArkUI.DrawableDescriptor" | [DrawableDescriptor](../apis-arkui/js-apis-arkui-drawableDescriptor.md) |
| "ArkUI.DragEvent" | [DragEvent](../apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#dragevent7)|
| "ArkUI.KeyEvent" | [KeyEvent](../apis-arkui/arkui-ts/ts-universal-events-key.md#keyevent对象说明)|
| "ArkUI.TouchEvent" | [TouchEvent](../apis-arkui/arkui-ts/ts-universal-events-touch.md#touchevent对象说明)|
| "ArkUI.MouseEvent" | [MouseEvent](../apis-arkui/arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)|
| "ArkUI.AxisEvent" | [AxisEvent](../apis-arkui/arkui-ts/ts-universal-events-axis.md#axisevent)|
| "ArkUI.ClickEvent" | [ClickEvent](../apis-arkui/arkui-ts/ts-universal-events-click.md#clickevent对象说明)|
| "ArkUI.HoverEvent" | [HoverEvent](../apis-arkui/arkui-ts/ts-universal-events-hover.md#hoverevent10对象说明)|
| "ArkUI.EventTargetInfo" | [EventTargetInfo](../apis-arkui/arkui-ts/ts-gesture-blocking-enhancement.md#eventtargetinfo)|
| "ArkUI.TouchTestInfo" | [TouchTestInfo](../apis-arkui/arkui-ts/ts-universal-attributes-on-child-touch-test.md#touchtestinfo)|
| "ArkUI.ScrollableTargetInfo" | [ScrollableTargetInfo](../apis-arkui/arkui-ts/ts-gesture-blocking-enhancement.md#scrollabletargetinfo)|
|"ArkUI.FrameNode" | [FrameNode](../apis-arkui/js-apis-arkui-frameNode.md)|
|"ArkUI.RenderNode" | [RenderNode](../apis-arkui/js-apis-arkui-renderNode.md)|
|"ArkUI.UIContext" | [UIContext](../apis-arkui/js-apis-arkui-UIContext.md)|
|"ArkUI.LengthMetrics" | [LengthMetrics](../apis-arkui/js-apis-arkui-graphics.md#lengthmetrics12)|
|"ArkUI.ShapeClip" | [ShapeClip](../apis-arkui/js-apis-arkui-graphics.md#shapeclip12)| 
|"ArkUI.ColorMetrics" | [ColorMetrics](../apis-arkui/js-apis-arkui-graphics.md#colormetrics12)|   
|"ArkUI.ShapeMask" | [ShapeMask](../apis-arkui/js-apis-arkui-graphics.md#shapemask12)|
| "ArkUI.ColorFilter" | [ColorFilter](../apis-arkui/arkui-ts/ts-types.md#colorfilter9) |
|"Global.Resource" | [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)|
| "ImageKit.AuxiliaryPicture" | [AuxiliaryPicture](../apis-image-kit/arkts-apis-image-AuxiliaryPicture.md) |
| "ImageKit.ImageCreator" | [ImageCreator](../apis-image-kit/arkts-apis-image-ImageCreator.md) |
| "ImageKit.ImagePacker" | [ImagePacker](../apis-image-kit/arkts-apis-image-ImagePacker.md) |
| "ImageKit.ImageReceiver" | [ImageReceiver](../apis-image-kit/arkts-apis-image-ImageReceiver.md) |
| "ImageKit.ImageSource" | [ImageSource](../apis-image-kit/arkts-apis-image-ImageSource.md) |
| "ImageKit.Picture" | [Picture](../apis-image-kit/arkts-apis-image-Picture.md) |
| "ImageKit.PixelMap" | [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) |
| "ArkGraphics3D.Animation" | [Animation](../apis-arkgraphics3d/js-apis-inner-scene-resources.md#animation)|
| "ArkGraphics3D.Environment" | [Environment](../apis-arkgraphics3d/js-apis-inner-scene-resources.md#environment)|
| "ArkGraphics3D.Camera" | [Camera](../apis-arkgraphics3d/js-apis-inner-scene-nodes.md#camera)|
| "ArkGraphics3D.Node" | [Node](../apis-arkgraphics3d/js-apis-inner-scene-nodes.md#node)|
| "ArkGraphics3D.Scene" | [Scene](../apis-arkgraphics3d/js-apis-inner-scene.md#scene-1)|
| "ArkGraphics3D.SceneResourceFactory" | [SceneResourceFactory](../apis-arkgraphics3d/js-apis-inner-scene.md#sceneresourcefactory)|
| "ArkWeb.FileSelectorParam" | [FileSelectorParam](../apis-arkweb/arkts-basic-components-web-FileSelectorParam.md)|
| "ArkWeb.FileSelectorResult" | [FileSelectorResult](../apis-arkweb/arkts-basic-components-web-FileSelectorResult.md)|
| "ArkWeb.JsResult" | [JsResult](../apis-arkweb/arkts-basic-components-web-JsResult.md)|
| "ArkWeb.WebContextMenuParam" | [WebContextMenuParam](../apis-arkweb/arkts-basic-components-web-WebContextMenuParam.md)|
| "ArkWeb.WebContextMenuResult" | [WebContextMenuResult](../apis-arkweb/arkts-basic-components-web-WebContextMenuResult.md)|
