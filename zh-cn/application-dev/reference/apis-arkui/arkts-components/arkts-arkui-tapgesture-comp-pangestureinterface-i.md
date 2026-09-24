# PanGestureInterface

```TypeScript
interface PanGestureInterface extends GestureInterface<PanGestureInterface>
```

滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。

**继承/实现关系：** PanGestureInterface extends GestureInterface<PanGestureInterface>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions): PanGestureInterface
```

创建滑动手势对象。继承自[GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: PanDirection; distance?: number } &#124; [PanGestureOptions](arkts-arkui-tapgesture-comp-pangestureoptions-c.md) | 否 | 滑动手势参数。<br> - fingers：用于指定触发滑动的最少手指数，最小为1指，最大取值为10指。<br>默认值：1<br>取值范围：[1, 10] <br>**说明：** <br>当设置的值小于1或不设置时，会被转化为默认值。<br> - direction：用于指定触发滑动的手势方向，此枚举值支持逻辑与(&amp;)和逻辑或（\&#124;）运算。<br>默认值：PanDirection.All <br> - distance：用于指定触发滑动手势事件的最小滑动距离，单位为vp。<br>取值范围：[0, +∞)<br>手写笔默认值：8，其余输入源默认值：5 <br>**说明：** <br>[Tabs](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs)组件滑动与该滑动手势事件同时存在时，可将distance值设为1，使滑动更灵敏，避免造成事件错乱。<br>当设定的值小于0时，按默认值处理。<br>当组件应用了[scale](arkts-arkui-common-comp-commonmethod-c.md#scale)缩放变换时，distance的实际识别距离会按照scale比例进行缩放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
(options?: PanGestureHandlerOptions): PanGestureInterface
```

创建滑动手势对象。与PanGesture | PanGestureOptions)}相比，options参数新增了对isFingerCountLimited和distanceMap参数，分别表示是否检查触摸屏幕的手指数量以及指定不同输入源触发滑动手势事件的最小滑动距离。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-tapgesture-comp-pangesturehandleroptions-i.md) | 否 | 滑动手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): PanGestureInterface
```

设置滑动手势取消回调。滑动手势识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滑动手势取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureInterface
```

设置滑动手势取消回调。滑动手势识别成功后，接收到触摸取消事件时触发回调。返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | 是 | 滑动手势取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势结束回调。滑动手势识别成功后，手指抬起时触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 滑动手势结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势识别成功回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 滑动手势识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势更新回调。fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 滑动手势更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) |  |
