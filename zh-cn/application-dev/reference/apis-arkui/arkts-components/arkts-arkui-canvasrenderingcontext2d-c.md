# CanvasRenderingContext2D

CanvasRenderingContext2D对象与Canvas组件绑定后，可在Canvas组件上绘制，绘制对象可以是形状、文本、图片等。
> **说明：**  
>  
> * 建议使用时将CanvasRenderingContext2D对象与Canvas组件封装到同一个自定义组件中，保证两者一一对应且生命周期保持一致。  
>  
> * 本文绘制接口在调用时会存入被关联的Canvas组件的指令队列中。仅当当前帧进入渲染阶段且关联的Canvas组件处于可见状态时，  
> 这些指令才会从队列中被提取并执行。因此，在Canvas组件不可见的情况下，应尽量避免频繁调用绘制接口，  
> 以防止指令在队列中堆积，从而避免内存占用过大的问题。  
>  
> * beginPath、moveTo、lineTo、closePath、bezierCurveTo、quadraticCurveTo、arc、arcTo、ellipse、rect和  
> roundRect接口只能对CanvasRenderingContext2D中的路径生效，无法对OffscreenCanvasRenderingContext2D和  
> Path2D对象中设置的路径生效。  
>  
> * Canvas组件的宽或高超过8000px时使用CPU渲染，会导致性能明显下降。

**继承/实现关系：** CanvasRenderingContext2D extends [CanvasRenderer](arkts-arkui-canvasrenderer-c.md)

**起始版本：** 8

<!--Device-unnamed-declare class CanvasRenderingContext2D extends CanvasRenderer--><!--Device-unnamed-declare class CanvasRenderingContext2D extends CanvasRenderer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(settings?: RenderingContextSettings)
```

构造Canvas画布对象，支持配置CanvasRenderingContext2D对象的参数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings)--><!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settings | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 否 | 用来配置CanvasRenderingContext2D对象的参数，见[RenderingContextSettings](#renderingcontextsettings)。<br>异常值undefined和null按[RenderingContextSettings](#renderingcontextsettings)的默认值处理。 |

## constructor

```TypeScript
constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)
```

构造Canvas画布对象，支持配置CanvasRenderingContext2D对象的参数和单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)--><!--Device-CanvasRenderingContext2D-constructor(settings?: RenderingContextSettings, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settings | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 否 | 用来配置CanvasRenderingContext2D对象的参数，见[RenderingContextSettings](#renderingcontextsettings)。<br>异常值undefined和null按[RenderingContextSettings](#renderingcontextsettings)的默认值处理。 |
| unit | [LengthMetricsUnit](../arkts-apis/arkts-arkui-graphics-lengthmetricsunit-e.md) | 否 | 用来配置CanvasRenderingContext2D对象的单位模式，配置后无法更改。<br>异常值undefined、NaN和Infinity按默认值处理。<br>默认值：DEFAULT。 |

## getContext2DFromDrawingContext

```TypeScript
static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D
```

从一个DrawingRenderingContext对象中获取一个CanvasRenderingContext2D对象，该CanvasRenderingContext2D对象与入参的DrawingRenderingContext对象绑定了相同的Canvas组件。
> **说明：**  
>  
> - 从该接口获取的CanvasRenderingContext2D对象不允许作为参数创建  
> [Canvas](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-canvas.md)  
> 组件，否则会导致应用崩溃。  
>  
> - 当入参的DrawingRenderingContext对象未绑定Canvas组件时，将返回错误码。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D--><!--Device-CanvasRenderingContext2D-static getContext2DFromDrawingContext(drawingContext: DrawingRenderingContext, options?: RenderingContextOptions): CanvasRenderingContext2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| drawingContext | [DrawingRenderingContext](arkts-arkui-drawingrenderingcontext-c.md) | 是 | 一个DrawingRenderingContext类型的对象。<br>异常值undefined或null按无效值处理。 |
| options | [RenderingContextOptions](arkts-arkui-renderingcontextoptions-i.md) | 否 | 渲染上下文的配置选项。<br>默认值：{ antialias: false } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) | 返回一个CanvasRenderingContext2D对象，其与入参的DrawingRenderingContext绑定了相同的Canvas组件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103702](../errorcode-canvas.md#103702-绘制上下文未绑定canvas组件) | The drawingContext is not bound to a canvas component. |

## off('onAttach')

```TypeScript
off(type: 'onAttach', callback?: Callback<void>): void
```

取消订阅CanvasRenderingContext2D与Canvas组件发生绑定的场景。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-off(type: 'onAttach', callback?: Callback<void>): void--><!--Device-CanvasRenderingContext2D-off(type: 'onAttach', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'onAttach' | 是 | 取消订阅CanvasRenderingContext2D与Canvas组件发生绑定的回调。<br>异常值undefined或null按无效值处理。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 为空表示取消所有订阅CanvasRenderingContext2D与Canvas组件发生绑定后触发的回调。非空则取消订阅发生绑定对应的回调。<br>异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Input parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## off('onDetach')

```TypeScript
off(type: 'onDetach', callback?: Callback<void>): void
```

取消订阅CanvasRenderingContext2D与Canvas组件解除绑定的场景。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-off(type: 'onDetach', callback?: Callback<void>): void--><!--Device-CanvasRenderingContext2D-off(type: 'onDetach', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'onDetach' | 是 | 取消订阅CanvasRenderingContext2D与Canvas组件解除绑定的回调。<br>异常值undefined或null按无效值处理。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 为空代表取消所有订阅CanvasRenderingContext2D与Canvas组件解除绑定后触发的回调。非空代表取消订阅解除绑定对应的回调。<br>异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Input parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## on('onAttach')

```TypeScript
on(type: 'onAttach', callback: Callback<void>): void
```

订阅CanvasRenderingContext2D与Canvas组件发生绑定的场景。
> **说明：**  
>  
> CanvasRenderingContext2D对象在同一时间只能与一个Canvas组件绑定。  
> 当CanvasRenderingContext2D对象和Canvas组件发生绑定时，会触发'onAttach'回调，  
> 表示可以获取到[canvas](#canvas13)。  
> 避免在'onAttach'中执行绘制方法，应保证Canvas组件已经  
> [onReady](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-canvas.md)  
> 再进行绘制。  
> 触发'onAttach'回调的一般场景：  
> 1、Canvas组件创建时绑定CanvasRenderingContext2D对象；  
> 2、CanvasRenderingContext2D对象新绑定一个Canvas组件时。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-on(type: 'onAttach', callback: Callback<void>): void--><!--Device-CanvasRenderingContext2D-on(type: 'onAttach', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'onAttach' | 是 | 订阅CanvasRenderingContext2D与Canvas组件发生绑定的回调。<br>异常值undefined或null按无效值处理。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 订阅CanvasRenderingContext2D与Canvas组件发生绑定后触发的回调。<br>异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Input parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## on('onDetach')

```TypeScript
on(type: 'onDetach', callback: Callback<void>): void
```

订阅CanvasRenderingContext2D与Canvas组件解除绑定的场景。
> **说明：**  
>  
> 当CanvasRenderingContext2D对象和Canvas组件解除绑定时，会触发'onDetach'回调，  
> 表示应停止绘制行为。  
> 触发'onDetach'回调的一般场景：  
> 1、Canvas组件销毁时解除绑定CanvasRenderingContext2D对象；  
> 2、CanvasRenderingContext2D对象新绑定一个Canvas组件，会先解除已有的绑定。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-on(type: 'onDetach', callback: Callback<void>): void--><!--Device-CanvasRenderingContext2D-on(type: 'onDetach', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'onDetach' | 是 | 订阅CanvasRenderingContext2D与Canvas组件解除绑定的回调。<br>异常值undefined或null按无效值处理。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 订阅CanvasRenderingContext2D与Canvas组件解除绑定后触发的回调。<br>异常值undefined或null按无效值处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Input parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |

## startImageAnalyzer

```TypeScript
startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>
```

配置并启动AI分析功能，使用Promise异步回调。使用前需先设置[enableAnalyzer](../../../reference/apis-arkui/arkui-ts/ts-components-canvas-canvas.md#enableanalyzer12)为true，启用图像AI分析能力。该方法调用时，将截取调用时刻的画面帧进行分析，使用时需注意启动分析的时机，避免出现画面和分析内容不一致的情况。未执行完重复调用该方法会触发错误回调。
> **说明：**  
>  
> 分析类型不支持动态修改。  
> 当检测到画面有变化时，分析结果将自动销毁，可重新调用本接口启动分析。  
> 该特性依赖设备能力，不支持该能力的情况下，将返回错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>--><!--Device-CanvasRenderingContext2D-startImageAnalyzer(config: ImageAnalyzerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | 是 | 执行AI分析所需要的入参，用于配置AI分析功能。<br>异常值undefined或null按无效值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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

停止AI分析功能，AI分析展示的内容将被销毁。
> **说明：**  
>  
> 在startImageAnalyzer方法未返回结果时调用本方法，会触发其错误回调。  
> 该特性依赖设备能力。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-stopImageAnalyzer(): void--><!--Device-CanvasRenderingContext2D-stopImageAnalyzer(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toDataURL

```TypeScript
toDataURL(type?: string, quality?: any): string
```

生成一个包含图片展示的URL，该接口存在内存拷贝行为，高耗时，应避免频繁使用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasRenderingContext2D-toDataURL(type?: string, quality?: any): string--><!--Device-CanvasRenderingContext2D-toDataURL(type?: string, quality?: any): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 否 | 用于指定图像格式。<br>可选参数为："image/png"，"image/jpeg"，"image/webp"。<br>异常值undefined或null按默认值处理。<br>默认值：image/png |
| quality | any | 否 | 在指定图片格式为image/jpeg或image/webp的情况下，可以从0到1的区间内选择图片的质量。如果超出取值范围，将会使用默认值0.92。<br>异常值undefined、null、NaN和Infinity按默认值处理。<br>默认值：0.92 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 图像的URL地址。 |

## canvas

```TypeScript
readonly canvas: FrameNode
```

获取和CanvasRenderingContext2D关联的Canvas组件的FrameNode实例。可用于监听关联Canvas组件的可见状态。<br>默认值：null。

**类型：** FrameNode

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-CanvasRenderingContext2D-readonly canvas: FrameNode--><!--Device-CanvasRenderingContext2D-readonly canvas: FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

组件高度。

默认单位为vp。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasRenderingContext2D-readonly height: number--><!--Device-CanvasRenderingContext2D-readonly height: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

组件宽度。

默认单位为vp。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasRenderingContext2D-readonly width: number--><!--Device-CanvasRenderingContext2D-readonly width: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

