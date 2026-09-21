# XComponentController

```TypeScript
declare class XComponentController
```

XComponent组件的控制器，可以将此对象绑定至XComponent组件，然后通过控制器来调用组件方法。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

XComponentController的构造函数。  
```ts
xComponentController: XComponentController = new XComponentController();
```

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
xComponentController: XComponentController = new XComponentController();
```

## getXComponentContext

```TypeScript
getXComponentContext(): Object
```

获取XComponent实例对象的context，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 获取XComponent实例对象的context，context包含的具体接口方法由开发者自定义，context内容与onLoad回调中的第一个参数一致。 |

## getXComponentSurfaceId

```TypeScript
getXComponentSurfaceId(): string
```

获取XComponent对应Surface的ID，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | XComponent持有Surface的ID。 |

**示例**

示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

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

获取XComponent持有Surface的显示区域，包括宽高和相对于组件左上角的位置坐标，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | 获取XComponent持有Surface的显示区域。 |

## getXComponentSurfaceRotation

```TypeScript
getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>
```

获取XComponent持有Surface在屏幕旋转时是否锁定方向的设置，仅XComponent类型为SURFACE("surface")时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Required&lt;[SurfaceRotationOptions](arkts-arkui-xcomponent-comp-surfacerotationoptions-i.md)&gt; | 获取XComponent持有Surface在屏幕旋转时是否锁定方向的设置。 |

## lockCanvas

```TypeScript
lockCanvas(): DrawingCanvas | null
```

返回可用于向XComponent上绘制内容的画布对象。具体绘制方法请参考Canvas。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) &#124; null | 可用于向XComponent区域绘制的画布对象；当无法获取画布对象时（如Surface未创建完成或画布已被占用未释放）返回null。 |

## onSurfaceChanged

```TypeScript
onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void
```

当XComponent持有的Surface大小改变后（包括首次创建时的大小改变）进行该回调，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |
| rect | [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | 是 | 回调该方法的时候，绑定XComponent持有Surface的显示区域。 |

## onSurfaceCreated

```TypeScript
onSurfaceCreated(surfaceId: string): void
```

当XComponent持有的Surface创建后进行该回调，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |

## onSurfaceDestroyed

```TypeScript
onSurfaceDestroyed(surfaceId: string): void
```

当XComponent持有的Surface销毁后进行该回调，仅XComponent类型为SURFACE("surface")或TEXTURE时有效，具体可以参考指南创建XComponent和管理Surface生命周期章节。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |

## setXComponentSurfaceConfig

```TypeScript
setXComponentSurfaceConfig(config: SurfaceConfig):void
```

设置XComponent创建的Surface的选项，用于设置XComponent持有的Surface在渲染时是否需要被视为不透明。当Surface绘制内容完全不透明时，可设置为不透明以提升渲染性能；当绘制内容包含透明区域时，需保持非不透明以保证透明效果正确显示。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [SurfaceConfig](arkts-arkui-xcomponent-comp-surfaceconfig-i.md) | 是 | Surface配置选项，用于设置XComponent持有的Surface在渲染时是否需要被视为不透明。 |

## setXComponentSurfaceRect

```TypeScript
setXComponentSurfaceRect(rect: SurfaceRect): void
```

设置XComponent持有Surface的显示区域，包括宽高和相对于组件左上角的位置坐标，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | [SurfaceRect](arkts-arkui-xcomponent-comp-surfacerect-i.md) | 是 | XComponent持有Surface的显示区域。 |

## setXComponentSurfaceRotation

```TypeScript
setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void
```

设置XComponent持有Surface在屏幕旋转时是否锁定方向，仅XComponent类型为SURFACE("surface")时有效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationOptions | [SurfaceRotationOptions](arkts-arkui-xcomponent-comp-surfacerotationoptions-i.md) | 是 | 设置XComponent持有Surface在屏幕旋转时是否锁定方向。 |

## setXComponentSurfaceSize

```TypeScript
setXComponentSurfaceSize(value: {
    surfaceWidth: number;
    surfaceHeight: number;
  }): void
```

设置XComponent持有Surface的宽度和高度，仅XComponent类型为SURFACE("surface")或TEXTURE时有效。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [setXComponentSurfaceRect](#setxcomponentsurfacerect)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | {     surfaceWidth: number;     surfaceHeight: number;   } | 是 | XComponent所持有的surface的宽度和高度。 |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

配置AI分析并启动AI分析功能，使用前需先启用图像AI分析能力enableAnalyzer，仅XComponent类型为SURFACE或TEXTURE时有效。使用Promise异步回调。<br>该方法调用时，将截取调用时刻的画面帧进行分析，使用时需注意启动分析的时机，避免出现画面和分析内容不一致的情况。<br>若该方法尚未执行完毕，此时重复调用，则会触发错误回调。以下错误码的详细介绍请参见图像AI分析错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | 是 | 执行AI分析所需要的入参，用于配置AI分析功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。用于获取AI分析是否成功执行。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [110001](../arkui-ts/errorcode-image-analyzer.md#110001-ai图像分析功能不支持) | Image analysis feature is unsupported. |
| [110002](../arkui-ts/errorcode-image-analyzer.md#110002-ai图像分析正在进行中) | Image analysis is currently being executed. |
| [110003](../arkui-ts/errorcode-image-analyzer.md#110003-ai图像分析已停止) | Image analysis is stopped. |

## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

停止AI分析功能，仅XComponent类型为SURFACE或TEXTURE时有效，须先调用enableAnalyzer和startImageAnalyzer启用AI分析能力。调用后AI分析展示的内容将被销毁。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unlockCanvasAndPost

```TypeScript
unlockCanvasAndPost(canvas: DrawingCanvas):void
```

将画布对象中的内容绘制在XComponent区域，并释放该画布对象。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | [DrawingCanvas](arkts-arkui-canvas-comp-drawingcanvas-t.md) | 是 | 之前调用lockCanvas方法返回的画布对象。 |
