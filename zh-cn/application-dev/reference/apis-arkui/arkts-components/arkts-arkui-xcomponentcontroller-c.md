# XComponentController

定义XComponent的控制器。 您可以将该控制器绑定到XComponent，以通过控制器调用组件接口。

**起始版本：** 8

<!--Device-unnamed-declare class XComponentController--><!--Device-unnamed-declare class XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

用于创建XComponentController实例的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-constructor()--><!--Device-XComponentController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
xComponentController: XComponentController = new XComponentController();
```

## getXComponentContext

```TypeScript
getXComponentContext(): Object
```

获取XComponent对象的context。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentContext(): Object--><!--Device-XComponentController-getXComponentContext(): Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | XComponent对象的context。 context中包含的接口由开发者定义。 context作为onLoad回调的第一个参数传入。 |

## getXComponentSurfaceId

```TypeScript
getXComponentSurfaceId(): string
```

获取XComponent所持有的surface的ID，可用于@ohos相关接口。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceId(): string--><!--Device-XComponentController-getXComponentSurfaceId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | XComponent所持有的surface的ID。 |

**示例**

```TypeScript
// xxx.ets

@Entry
  @Component
  struct Index {
    myXComponentController: XComponentController = new XComponentController();

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        XComponent({
          type: XComponentType.SURFACE,
          controller: this.myXComponentController
        })
          .onLoad(() => {
            let surfaceId: string = this.myXComponentController.getXComponentSurfaceId();
            console.info("XComponent SurfaceId: " + surfaceId);
          })
      }
    }
  }
```

## getXComponentSurfaceRect

```TypeScript
getXComponentSurfaceRect(): SurfaceRect
```

获取XComponent所持有的surface的矩形。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect--><!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SurfaceRect](arkts-arkui-surfacerect-i.md) | XComponent所持有的surface的矩形。 |

## getXComponentSurfaceRotation

```TypeScript
getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>
```

获取屏幕旋转时此XComponent所持有的surface的方向是否锁定。 该接口仅在XComponent的type设置为SURFACE("surface")时生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>--><!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Required&lt;[SurfaceRotationOptions](arkts-arkui-surfacerotationoptions-i.md)&gt; | surface旋转选项的结果。 |

## lockCanvas

```TypeScript
lockCanvas(): DrawingCanvas | null
```

获取用于在XComponent创建的surface上绘制的Canvas。有关绘制方法的详细信息，请参见[Canvas](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-canvas-c.md)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-lockCanvas(): DrawingCanvas | null--><!--Device-XComponentController-lockCanvas(): DrawingCanvas | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawingCanvas](../arkts-apis/arkts-arkui-drawingcanvas-t.md) | 返回用于在XComponent创建的surface上绘制的Canvas。 如果surface不可用，则返回null。 |

## onSurfaceChanged

```TypeScript
onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void
```

当XComponent所持有的surface大小发生变化时触发（包括XComponent以指定大小创建时）。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。 **说明：** 仅当XComponent组件未设置libraryname参数时，会进行该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void--><!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent所持有的surface的ID。 |
| rect | [SurfaceRect](arkts-arkui-surfacerect-i.md) | 是 | 用于显示XComponent所持有的surface的矩形。 |

## onSurfaceCreated

```TypeScript
onSurfaceCreated(surfaceId: string): void
```

当XComponent所持有的surface创建完成时触发。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。 **说明：** 仅当XComponent组件未设置libraryname参数时，会进行该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void--><!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent所持有的surface的ID。 |

## onSurfaceDestroyed

```TypeScript
onSurfaceDestroyed(surfaceId: string): void
```

当XComponent所持有的surface销毁时触发。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。 **说明：** 仅当XComponent组件未设置libraryname参数时，会进行该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void--><!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | XComponent所持有的surface的ID。 |

## setXComponentSurfaceConfig

```TypeScript
setXComponentSurfaceConfig(config: SurfaceConfig):void
```

设置XComponent创建的surface的配置。 > **说明：** > > 此接口仅在XComponent的type为TEXTURE或SURFACE时生效。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void--><!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [SurfaceConfig](arkts-arkui-surfaceconfig-i.md) | 是 | surface配置 |

## setXComponentSurfaceRect

```TypeScript
setXComponentSurfaceRect(rect: SurfaceRect): void
```

设置XComponent所持有的surface的矩形。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void--><!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | [SurfaceRect](arkts-arkui-surfacerect-i.md) | 是 | XComponent所持有的surface的矩形。 |

## setXComponentSurfaceRotation

```TypeScript
setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void
```

设置屏幕旋转时是否锁定此XComponent所持有的surface的方向。 该接口仅在XComponent的type设置为SURFACE("surface")时生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void--><!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationOptions | [SurfaceRotationOptions](arkts-arkui-surfacerotationoptions-i.md) | 是 | 屏幕旋转时是否锁定当前XComponent所持有的surface的方向。 |

## setXComponentSurfaceSize

```TypeScript
setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void
```

设置XComponent所持有的surface的宽度和高度。 该接口仅在XComponent的type设置为SURFACE("surface")或TEXTURE时生效。 单位：px。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setXComponentSurfaceRect](#setxcomponentsurfacerect)

<!--Device-XComponentController-setXComponentSurfaceSize(value: {    surfaceWidth: number;    surfaceHeight: number;  }): void--><!--Device-XComponentController-setXComponentSurfaceSize(value: {    surfaceWidth: number;    surfaceHeight: number;  }): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     surfaceWidth: number;     surfaceHeight: number;   } | 是 | XComponent所持有的surface的宽度和高度。 |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

配置AI分析并启动AI分析功能，使用前需先启用图像AI分析能力[enableAnalyzer](arkts-arkui-xcomponent-attribute.md#enableanalyzer)，仅type为SURFACE或TEXTURE时有效。使用Promise异步回调来返回结果。 由于用于分析的图像帧是调用此接口时捕获的帧，因此请注意此接口的调用时机。 如果在执行完成之前重复调用此接口，将触发错误回调。 > **说明：** > 图像分析类型无法动态修改。 > > 此接口依赖于设备能力。在不兼容的设备上调用将返回错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | ImageAnalyzerConfig | 是 | AI图像分析器的设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 用于返回结果的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [110001](../arkui-ts/errorcode-image-analyzer.md#110001-ai图像分析功能不支持) | 不支持图像分析特性。 |
| [110003](../arkui-ts/errorcode-image-analyzer.md#110003-ai图像分析已停止) | 图像分析已停止。 |
| [110002](../arkui-ts/errorcode-image-analyzer.md#110002-ai图像分析正在进行中) | 图像分析正在执行中。 |

## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

停止AI分析功能，AI分析展示的内容将被销毁。仅type为SURFACE或TEXTURE时有效。 > **说明：** > 如果在startImageAnalyzer接口尚未返回任何结果时调用此接口，将触发错误回调。 > > 此特性依赖于设备能力。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-XComponentController-stopImageAnalyzer(): void--><!--Device-XComponentController-stopImageAnalyzer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
| canvas | [DrawingCanvas](../arkts-apis/arkts-arkui-drawingcanvas-t.md) | 是 | 之前通过lockCanvas获取的canvas。 |

