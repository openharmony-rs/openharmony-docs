# XComponentController

XComponent组件的控制器，可以将此对象绑定至XComponent组件，然后通过控制器来调用组件方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class XComponentController--><!--Device-unnamed-export declare class XComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

XComponentController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-constructor()--><!--Device-XComponentController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getXComponentSurfaceId

```TypeScript
getXComponentSurfaceId(): string
```

获取XComponent对应Surface的ID，仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-getXComponentSurfaceId(): string--><!--Device-XComponentController-getXComponentSurfaceId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | XComponent持有Surface的ID。 |

## getXComponentSurfaceRect

```TypeScript
getXComponentSurfaceRect(): SurfaceRect
```

获取XComponent持有Surface的显示区域，包括宽高和相对于组件左上角的位置坐标， 仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect--><!--Device-XComponentController-getXComponentSurfaceRect(): SurfaceRect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 获取XComponent持有Surface的显示区域。 |

## getXComponentSurfaceRotation

```TypeScript
getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>
```

获取XComponent持有Surface在屏幕旋转时是否锁定方向的设置， 仅XComponent类型为SURFACE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>--><!--Device-XComponentController-getXComponentSurfaceRotation(): Required<SurfaceRotationOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Required&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 获取XComponent持有Surface在屏幕旋转时是否锁定方向的设置。 |

## lockCanvas

```TypeScript
lockCanvas(): DrawingCanvas | null
```

返回可用于向XComponent上绘制内容的画布对象。只支持TEXTURE和SURFACE模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-lockCanvas(): DrawingCanvas | null--><!--Device-XComponentController-lockCanvas(): DrawingCanvas | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 可用于向XComponent区域绘制的画布对象或者空对象null。 |

## onSurfaceChanged

```TypeScript
onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void
```

当XComponent持有的Surface大小改变后（包括首次创建时的大小改变）进行该回调， 仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void--><!--Device-XComponentController-onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调该方法的时候，绑定XComponent持有Surface的显示区域。 |

## onSurfaceCreated

```TypeScript
onSurfaceCreated(surfaceId: string): void
```

当XComponent持有的Surface创建后进行该回调，仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void--><!--Device-XComponentController-onSurfaceCreated(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |

## onSurfaceDestroyed

```TypeScript
onSurfaceDestroyed(surfaceId: string): void
```

当XComponent持有的Surface销毁后进行该回调，仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void--><!--Device-XComponentController-onSurfaceDestroyed(surfaceId: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 回调该方法的时候，绑定XComponent持有Surface的ID。 |

## setXComponentSurfaceConfig

```TypeScript
setXComponentSurfaceConfig(config: SurfaceConfig):void
```

设置XComponent创建的Surface的选项，用于设置XComponent持有的Surface在渲染时是否需要被视为不透明。 当Surface绘制内容完全不透明时，可设置为不透明以提升渲染性能；当绘制内容包含透明区域时， 需保持非不透明以保证透明效果正确显示。仅当XComponent组件类型为TEXTURE或SURFACE时，本接口生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void--><!--Device-XComponentController-setXComponentSurfaceConfig(config: SurfaceConfig):void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Surface配置选项，用于设置XComponent持有的Surface在渲染时是否需要被视为不透明。 |

## setXComponentSurfaceRect

```TypeScript
setXComponentSurfaceRect(rect: SurfaceRect): void
```

设置XComponent持有Surface的显示区域，包括宽高和相对于组件左上角的位置坐标， 仅XComponent类型为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void--><!--Device-XComponentController-setXComponentSurfaceRect(rect: SurfaceRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | XComponent持有Surface的显示区域。 |

## setXComponentSurfaceRotation

```TypeScript
setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void
```

设置XComponent持有Surface在屏幕旋转时是否锁定方向， 仅XComponent类型为SURFACE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void--><!--Device-XComponentController-setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设置XComponent持有Surface在屏幕旋转时是否锁定方向。 |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

配置AI分析并启动AI分析功能，使用前需先启用图像AI分析能力enableAnalyzer， 仅type为SURFACE或TEXTURE时有效。使用Promise异步回调。 该方法调用时，将截取调用时刻的画面帧进行分析，使用时需注意启动分析的时机， 避免出现画面和分析内容不一致的情况。若该方法尚未执行完毕，此时重复调用， 则会触发错误回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-XComponentController-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 执行AI分析所需要的入参，用于配置AI分析功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。用于获取AI分析是否成功执行。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [110001](../../arkui-ts/errorcode-image-analyzer.md#110001-ai图像分析功能不支持) | 不支持图像分析特性。 |
| [110002](../../arkui-ts/errorcode-image-analyzer.md#110002-ai图像分析正在进行中) | 图像分析正在执行中。 |
| [110003](../../arkui-ts/errorcode-image-analyzer.md#110003-ai图像分析已停止) | 图像分析已停止。 |

## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

停止AI分析功能，AI分析展示的内容将被销毁。仅type为SURFACE或TEXTURE时有效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-stopImageAnalyzer(): void--><!--Device-XComponentController-stopImageAnalyzer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unlockCanvasAndPost

```TypeScript
unlockCanvasAndPost(canvas: DrawingCanvas): void
```

将画布对象中的内容绘制在XComponent区域，并释放该画布对象。只支持TEXTURE和SURFACE模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas): void--><!--Device-XComponentController-unlockCanvasAndPost(canvas: DrawingCanvas): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| canvas | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 之前调用lockCanvas方法返回的画布对象。 |

