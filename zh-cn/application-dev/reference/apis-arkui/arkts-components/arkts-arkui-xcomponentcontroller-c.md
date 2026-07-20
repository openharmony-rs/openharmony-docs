# XComponentController

定义XComponent的控制器。您可以将该控制器绑定到XComponent，以通过控制器调用组件接口。

**起始版本：** 12

<!--Device-unnamed-declare class XComponentController--><!--Device-unnamed-declare class XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

用于创建XComponentController实例的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-constructor()--><!--Device-XComponentController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getxcomponentcontext"></a>
## getXComponentContext

```TypeScript
getXComponentContext(): Object
```

获取XComponent对象的context。该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentContext(): Object--><!--Device-XComponentController-getXComponentContext(): Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | XComponent对象的context。context中包含的接口由开发者定义。context作为onLoad回调的第一个参数传入。 |

<a id="getxcomponentsurfaceid"></a>
## getXComponentSurfaceId

```TypeScript
getXComponentSurfaceId(): string
```

获取XComponent所持有的surface的ID，可用于@ohos相关接口。该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceId(): string--><!--Device-XComponentController-getXComponentSurfaceId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | XComponent所持有的surface的ID。 |

<a id="getxcomponentsurfacerect"></a>
## getXComponentSurfaceRect

```TypeScript
getXComponentSurfaceRect(): SurfaceRect
```

获取XComponent创建的surface的矩形信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect--><!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SurfaceRect](arkts-arkui-surfacerect-i.md) | surface的矩形信息。 |

<a id="getxcomponentsurfacerotation"></a>
## getXComponentSurfaceRotation

```TypeScript
getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>
```

获取XComponent创建的Surface的旋转选项结果。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>--><!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Required&lt;SurfaceRotationOptions&gt; | surface旋转选项的结果。 |

<a id="lockcanvas"></a>
## lockCanvas

```TypeScript
lockCanvas(): DrawingCanvas | null
```

获取用于在XComponent创建的surface上绘制的Canvas。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-lockCanvas(): DrawingCanvas | null--><!--Device-XComponentController-lockCanvas(): DrawingCanvas | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawingCanvas](arkts-arkui-drawingcanvas-t.md) | 返回用于在XComponent创建的surface上绘制的Canvas。如果surface不可用，则返回null。 |

<a id="onsurfacechanged"></a>
## onSurfaceChanged

```TypeScript
onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void
```

当surface矩形信息发生变化后回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void--><!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent创建的surface的id。 |
| rect | [SurfaceRect](arkts-arkui-surfacerect-i.md) | 是 | XComponent创建的surface的矩形信息。 |

<a id="onsurfacecreated"></a>
## onSurfaceCreated

```TypeScript
onSurfaceCreated(surfaceId: string): void
```

当surface首次创建完成后回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void--><!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent创建的surface的id。 |

<a id="onsurfacedestroyed"></a>
## onSurfaceDestroyed

```TypeScript
onSurfaceDestroyed(surfaceId: string): void
```

当surface即将被销毁时回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void--><!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent创建的surface的id。 |

<a id="setxcomponentsurfaceconfig"></a>
## setXComponentSurfaceConfig

```TypeScript
setXComponentSurfaceConfig(config: SurfaceConfig):void
```

设置XComponent创建的surface的配置。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void--><!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [SurfaceConfig](arkts-arkui-surfaceconfig-i.md) | 是 | surface配置 |

<a id="setxcomponentsurfacerect"></a>
## setXComponentSurfaceRect

```TypeScript
setXComponentSurfaceRect(rect: SurfaceRect): void
```

设置XComponent创建的surface的矩形信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void--><!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | [SurfaceRect](arkts-arkui-surfacerect-i.md) | 是 | surface的矩形信息。 |

<a id="setxcomponentsurfacerotation"></a>
## setXComponentSurfaceRotation

```TypeScript
setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void
```

设置XComponent创建的Surface的旋转选项。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void--><!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationOptions | [SurfaceRotationOptions](arkts-arkui-surfacerotationoptions-i.md) | 是 | surface的旋转选项。 |

<a id="setxcomponentsurfacesize"></a>
## setXComponentSurfaceSize

```TypeScript
setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void
```

设置XComponent所持有的surface的宽度和高度。该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setXComponentSurfaceRect](arkts-arkui-xcomponentcontroller-c.md#setxcomponentsurfacerect-1)

<!--Device-XComponentController-setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void--><!--Device-XComponentController-setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     surfaceWidth: number;     surfaceHeight: number;   } | 是 | XComponent所持有的surface的宽度和高度。 |

<a id="startimageanalyzer"></a>
## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

在给定设置中启动AI图像分析。调用此接口前，请确保已启用AI图像分析器。由于用于分析的图像帧是调用此接口时捕获的帧，因此请注意此接口的调用时机。如果在执行完成之前重复调用此接口，将触发错误回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | 是 | AI图像分析器的设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 用于返回结果的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [110001](../arkui-ts/errorcode-image-analyzer.md#110001-ai图像分析功能不支持) | 不支持图像分析特性。 |
| [110002](../arkui-ts/errorcode-image-analyzer.md#110002-ai图像分析正在进行中) | 图像分析正在执行中。 |
| [110003](../arkui-ts/errorcode-image-analyzer.md#110003-ai图像分析已停止) | 图像分析已停止。 |

<a id="stopimageanalyzer"></a>
## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

停止AI图像分析。AI图像分析器显示的内容将被销毁。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-stopImageAnalyzer(): void--><!--Device-XComponentController-stopImageAnalyzer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="unlockcanvasandpost"></a>
## unlockCanvasAndPost

```TypeScript
unlockCanvasAndPost(canvas: DrawingCanvas):void
```

将Canvas的新内容发布到XComponent创建的surface，并释放该Canvas。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas):void--><!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas):void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | [DrawingCanvas](arkts-arkui-drawingcanvas-t.md) | 是 | 之前通过lockCanvas获取的canvas。 |

