# CanvasRenderingContext2D

CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制， 绘制对象可以是形状、文本、图片等。

**继承/实现关系：** CanvasRenderingContext2D extends [CanvasRenderer](arkts-na-canvas-canvasrenderer-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class CanvasRenderingContext2D--><!--Device-unnamed-export declare class CanvasRenderingContext2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)
```

构造Canvas画布对象，支持配置CanvasRenderingContext2D对象的参数和单位模式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)--><!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settings | [RenderingContextSettings](arkts-na-canvas-renderingcontextsettings-c.md) | 否 | 用来配置CanvasRenderingContext2D对象的参数， 见RenderingContextSettings。 异常值undefined和null按RenderingContextSettings的默认值处理。 |
| unit | [LengthMetricsUnit](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | 否 | 用来配置CanvasRenderingContext2D对象的单位模式， 配置后无法更改。异常值undefined、NaN和Infinity按默认值处理。默认值：DEFAULT。 |

## getContext2DFromDrawingContext

```TypeScript
static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D
```

从一个DrawingRenderingContext对象中获取一个CanvasRenderingContext2D对象， 该CanvasRenderingContext2D对象与入参的DrawingRenderingContext对象绑定了相同的Canvas组件。 > **说明：** > > - 从该接口获取的CanvasRenderingContext2D对象不允许作为参数创建Canvas组件， > 否则会导致应用崩溃。 > > - 当入参的DrawingRenderingContext对象未绑定Canvas组件时，将返回错误码。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D--><!--Device-CanvasRenderingContext2D-static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawingContext | [DrawingRenderingContext](arkts-na-canvas-drawingrenderingcontext-c.md) | 是 | 一个DrawingRenderingContext类型的对象。 |
| options | [RenderingContextOptions](arkts-na-canvas-renderingcontextoptions-i.md) | 否 | 渲染上下文的配置选项。 默认值：{ antialias: false }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasRenderingContext2D](arkts-na-canvas-canvasrenderingcontext2d-c.md) | 返回一个CanvasRenderingContext2D对象， 其与入参的DrawingRenderingContext绑定了相同的Canvas组件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103702](../../apis-arkui/errorcode-canvas.md#103702-绘制上下文未绑定canvas组件) | The drawingContext is not bound to a canvas component. @static |

## offAttach

```TypeScript
offAttach(callback?: VoidCallback): void
```

取消订阅CanvasRenderingContext2D与Canvas组件发生绑定的场景。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-offAttach(callback?: VoidCallback): void--><!--Device-CanvasRenderingContext2D-offAttach(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 否 | 为空表示取消所有订阅CanvasRenderingContext2D与Canvas组件 发生绑定后触发的回调。非空则取消订阅发生绑定对应的回调。 异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## offDetach

```TypeScript
offDetach(callback?: VoidCallback): void
```

取消订阅CanvasRenderingContext2D与Canvas组件解除绑定的场景。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-offDetach(callback?: VoidCallback): void--><!--Device-CanvasRenderingContext2D-offDetach(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 否 | 为空代表取消所有订阅CanvasRenderingContext2D与Canvas组件 解除绑定后触发的回调。非空代表取消订阅解除绑定对应的回调。 异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## onAttach

```TypeScript
onAttach(callback: VoidCallback): void
```

订阅CanvasRenderingContext2D与Canvas组件发生绑定的场景。 > **说明：** > > CanvasRenderingContext2D对象在同一时间只能与一个Canvas组件绑定。 > 当CanvasRenderingContext2D对象和Canvas组件发生绑定时，会触发'onAttach'回调， > 表示可以获取到canvas。 > 避免在'onAttach'中执行绘制方法，应保证Canvas组件已经'onReady'再进行绘制。 > 触发'onAttach'回调的一般场景： > 1、Canvas组件创建时绑定CanvasRenderingContext2D对象; > 2、CanvasRenderingContext2D对象新绑定一个Canvas组件时。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-onAttach(callback: VoidCallback): void--><!--Device-CanvasRenderingContext2D-onAttach(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 订阅CanvasRenderingContext2D与Canvas组件发生绑定后 触发的回调。异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## onDetach

```TypeScript
onDetach(callback: VoidCallback): void
```

订阅CanvasRenderingContext2D与Canvas组件解除绑定的场景。 > **说明：** > > 当CanvasRenderingContext2D对象和Canvas组件解除绑定时，会触发'onDetach'回调， > 表示应停止绘制行为。 > 触发'onDetach'回调的一般场景： > 1、Canvas组件销毁时解除绑定CanvasRenderingContext2D对象; > 2、CanvasRenderingContext2D对象新绑定一个Canvas组件，会先解除已有的绑定。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-onDetach(callback: VoidCallback): void--><!--Device-CanvasRenderingContext2D-onDetach(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 订阅CanvasRenderingContext2D与Canvas组件解除绑定后 触发的回调。异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

配置并启动AI分析功能，使用Promise异步回调。 使用前需先设置enableAnalyzer为true，启用图像AI分析能力。 该方法调用时，将截取调用时刻的画面帧进行分析，使用时需注意启动分析的时机， 避免出现画面和分析内容不一致的情况。 未执行完重复调用该方法会触发错误回调。 > **说明：** > > 分析类型不支持动态修改。 > 当检测到画面有变化时，分析结果将自动销毁，可重新调用本接口启动分析。 > 该特性依赖设备能力，不支持该能力的情况下，将返回错误码。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-CanvasRenderingContext2D-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](arkts-na-imagecommon-imageanalyzerconfig-i.md) | 是 | 执行AI分析所需要的入参，用于配置AI分析功能。 异常值undefined或null按无效值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [110001](../../apis-arkui/arkui-ts/errorcode-image-analyzer.md#110001-ai图像分析功能不支持) | Image analysis feature is not supported. |
| [110003](../../apis-arkui/arkui-ts/errorcode-image-analyzer.md#110003-ai图像分析已停止) | Image analysis is stopped. |
| [110002](../../apis-arkui/arkui-ts/errorcode-image-analyzer.md#110002-ai图像分析正在进行中) | Image analysis is currently being executed. |

## stopImageAnalyzer

```TypeScript
stopImageAnalyzer(): void
```

停止AI分析功能，AI分析展示的内容将被销毁。 > **说明：** > > 在startImageAnalyzer方法未返回结果时调用本方法，会触发其错误回调。 > 该特性依赖设备能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-stopImageAnalyzer(): void--><!--Device-CanvasRenderingContext2D-stopImageAnalyzer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toDataURL

```TypeScript
toDataURL(type?: string, quality?: double): string
```

生成一个包含图片展示的URL，该接口存在内存拷贝行为，高耗时，应避免频繁使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasRenderingContext2D-toDataURL(type?: string, quality?: double): string--><!--Device-CanvasRenderingContext2D-toDataURL(type?: string, quality?: double): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 否 | 用于指定图像格式。可选参数为："image/png"，"image/jpeg"， "image/webp"。异常值undefined或null按默认值处理。默认值：image/png。 |
| quality | double | 否 | 在指定图片格式为image/jpeg或image/webp的情况下， 可以从0到1的区间内选择图片的质量。如果超出取值范围， 将会使用默认值0.92。异常值undefined、null、NaN和Infinity按默认值处理。 默认值：0.92。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 图像的URL地址。 |

