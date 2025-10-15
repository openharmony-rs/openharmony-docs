# 手势处理器
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

用于设置组件绑定的手势。可以通过[UIGestureEvent](./ts-uigestureevent.md#uigestureevent)对象调用其接口添加或删除手势。

>**说明：**
>
>本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## GestureHandler\<T>

手势处理器的基础类型。

### tag

tag(tag: string): T

设置手势处理器的标志。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 |说明                                        |
| ----  | ------  | ------|---------------------------------- |
| tag   | string  | 是 |手势处理器的标志。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

### allowedTypes<sup>14+</sup>

allowedTypes(types: Array\<SourceTool>): T

设置手势处理器所支持的事件输入源。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 |说明                                        |
| ----  | ------  | ------|---------------------------------- |
| types   | Array\<[SourceTool](ts-gesture-settings.md#sourcetool枚举说明9)>  | 是 |手势处理器所支持的事件输入源。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## BaseHandlerOptions<sup>15+</sup>

基础手势处理器配置参数。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型          | 只读 | 可选 | 说明            |
|---------------|---------------|-----|------|----------------|
| isFingerCountLimited | boolean | 否 | 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。<br>默认值：false |

## TapGestureHandler

点击手势处理器对象类型。

### constructor

constructor(options?: TapGestureHandlerOptions)

点击手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [TapGestureHandlerOptions](#tapgesturehandleroptions) | 否   | 点击手势处理器配置参数。 |

### onAction

onAction(event: Callback\<GestureEvent>): TapGestureHandler

设置点击手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 点击手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [TapGestureHandler](#tapgesturehandler) | 返回当前点击手势处理器对象。 |

## TapGestureHandlerOptions

点击手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                                  | 只读 | 可选 | 说明                 |
| ------------ | -------------------------------------|------ | ---- | -------------------- |
| count | number | 否 | 是 | 识别的连续点击次数。当设置的值小于1或不设置时，会被转化为默认值。<br/>默认值：1<br/>取值范围：[0, +∞)<br/>**说明：**<br/>1. 当配置多击时，上一次的最后一根手指抬起和下一次的第一根手指按下的超时时间为300毫秒。<br/>2. 当上次点击的位置与当前点击的位置距离超过60vp时，手势识别失败。|
| fingers | number | 否 | 是 | 触发点击的手指数，最小为1指，&nbsp;最大为10指。当设置小于1的值或不设置时，会被转化为默认值。<br/>默认值：1<br/>**说明：**<br/>1. 当配置多指时，第一根手指按下后300毫秒内未有足够的手指数按下，手势识别失败，第一根手指抬起后300毫秒内未有足够的手指抬起，手势识别失败。<br/>2. 实际点击手指数超过配置值，手势识别成功。 |
| isFingerCountLimited<sup>15+</sup> | boolean | 否 | 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。如果触摸手指的数量不等于设置的触发点击的手指数（即上述fingers参数），那么该手势识别失败。<br>在多击事件中（上述count参数大于1），需要每一次点击的手指数都等于设置的触发点击的手指数，否则该手势识别失败。<br>默认值：false<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## LongPressGestureHandler

长按手势处理器对象类型。

### constructor

constructor(options?: LongPressGestureHandlerOptions)

长按手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**


| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [LongPressGestureHandlerOptions](#longpressgesturehandleroptions) | 否   | 长按手势处理器配置参数。 |

### onAction

onAction(event: Callback\<GestureEvent>): LongPressGestureHandler

设置长按手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 长按手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | 返回当前长按手势处理器对象。 |

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): LongPressGestureHandler

设置长按手势处理器结束回调。长按手势处理器识别成功后，最后一根手指抬起时触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 长按手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | 返回当前长按手势处理器对象。 |

### onActionCancel

onActionCancel(event: Callback\<void>): LongPressGestureHandler

设置长按手势处理器取消回调。长按手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | 是 | 长按手势处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | 返回当前长按手势处理器对象。 |

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): LongPressGestureHandler

设置长按手势处理器取消回调。长按手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](#onactioncancel)接口相比，此接口返回手势事件信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 长按手势处理器取消回调。该回调会返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | 返回当前长按手势处理器对象。 |

## LongPressGestureHandlerOptions

长按手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                               | 只读    | 可选 | 说明                 |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | 否| 是 | 触发长按的最少手指数，最小为1指，&nbsp;最大取值为10指。<br/>默认值：1 <br/>取值范围：[1, 10]<br/> **说明：** <br/>手指按下后若发生超过15px的移动，则判定当前长按手势识别失败。|
| repeat | boolean | 否| 是 | 是否连续触发事件回调。true表示为连续触发事件回调，false表示不连续触发事件回调。<br/>默认值：false |
| duration | number | 否| 是 | 触发长按的最短时间，单位为毫秒（ms）。<br/>默认值：500 <br/>**说明：** <br/>取值范围：[0, +∞)，设置小于等于0时，按照默认值500处理。|
| isFingerCountLimited<sup>15+</sup> | boolean | 否| 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。若触摸屏幕的手指的数量不等于设置的触发长按的最少手指数（即上述fingers参数），手势识别将失败。<br>对于已成功识别的手势，后续触摸屏幕的手指数变化，将不触发repeat事件（若触摸屏幕的手指数恢复到设置的触发长按的最少手指数时，可以触发[onAction](ts-basic-gestures-longpressgesture.md#事件)事件），但可以触发[onActionEnd](ts-basic-gestures-longpressgesture.md#事件)事件。<br>默认值：false<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## PanGestureHandler

滑动手势处理器对象类型。

### constructor

constructor(options?: PanGestureHandlerOptions)

滑动手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**


| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [PanGestureHandlerOptions](#pangesturehandleroptions) | 否   | 滑动手势处理器配置参数。 |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): PanGestureHandler

设置滑动手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 滑动手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | 返回当前滑动手势处理器对象。 |

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): PanGestureHandler

设置滑动手势处理器更新回调。滑动手势处理器移动过程中触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 滑动手势处理器更新回调。<br/>fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | 返回当前滑动手势处理器对象。 |

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): PanGestureHandler

设置滑动手势处理器结束回调。滑动手势处理器识别成功后，手指抬起时触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 滑动手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | 返回当前滑动手势处理器对象。 |

### onActionCancel

onActionCancel(event: Callback\<void>): PanGestureHandler

设置滑动手势处理器取消回调。滑动手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | 是 | 滑动手势处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | 返回当前滑动手势处理器对象。 |

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): PanGestureHandler

设置滑动手势处理器取消回调。滑动手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](#onactioncancel-1)接口相比，此接口返回手势事件信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 滑动手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | 返回当前滑动手势处理器对象。 |

## PanGestureHandlerOptions

滑动手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                              | 只读 | 可选 | 说明                 |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | 否| 是 | 用于指定触发拖动的最少手指数，最小为1指，&nbsp;最大取值为10指。<br/>默认值：1<br/>取值范围：[1, 10]<br/>**说明：** <br/>当设置的值小于1或不设置时，会被转化为默认值。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| direction | [PanDirection](./ts-basic-gestures-pangesture.md#pandirection枚举说明) | 否| 是 | 用于指定触发拖动的手势方向，此枚举值支持逻辑与(&amp;)和逻辑或（\|）运算。<br/>默认值：PanDirection.All<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| distance | number | 否| 是 | 用于指定触发滑动手势事件的最小拖动距离，单位为vp。<br/>手写笔默认值：8，其余输入源默认值：5<br/>**说明：**<br/>[Tabs组件](ts-container-tabs.md)滑动与该滑动手势事件同时存在时，可将distance值设为1，使拖动更灵敏，避免造成事件错乱。<br/>取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。<br/>从API version 19开始，手写笔默认值为8，单位为vp。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| distanceMap<sup>19+</sup> |  Map<[SourceTool](ts-gesture-settings.md#sourcetool枚举说明9), number> | 否| 是 | 用于指定不同输入源触发滑动手势事件的最小拖动距离，单位为vp。<br/>手写笔默认值：8，其余输入源默认值：5<br/>取值范围：[0, +∞)，当设定的值小于0时，按默认值处理。<br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |

## SwipeGestureHandler

快滑手势处理器对象类型。

### constructor

constructor(options?: SwipeGestureHandlerOptions)

快滑手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [SwipeGestureHandlerOptions](#swipegesturehandleroptions) | 否   | 快滑手势处理器配置参数。 |

### onAction

onAction(event: Callback\<GestureEvent>): SwipeGestureHandler

设置快滑手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 快滑手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [SwipeGestureHandler](#swipegesturehandler) | 返回当前快滑手势处理器对象。 |

## SwipeGestureHandlerOptions

快滑手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                                   | 只读 | 可选 | 说明                 |
| ------------ | -------------------------------------- | ---- | -----|--------------- |
| fingers | number | 否 | 是 | 触发快滑的最少手指数，默认为1，最小为1指，最大为10指。<br/>默认值：1 <br/>取值范围：[1, 10]<br/> |
| direction | [SwipeDirection](./ts-basic-gestures-swipegesture.md#swipedirection枚举说明) | 否 | 是 | 触发快滑手势的滑动方向。<br/>默认值：SwipeDirection.All |
| speed | number | 否 | 是 | 识别快滑的最小速度。<br/>默认值：100VP/s <br/>**说明：** <br/>当滑动速度的值小于等于0时，会被转化为默认值。 |
| isFingerCountLimited<sup>15+</sup> | boolean | 否 | 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。如果触摸手指的数量不等于设置的触发滑动的最少手指数（即上述fingers参数），手势识别将失败。<br>默认值：false<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## PinchGestureHandler

捏合手势处理器对象类型。

### constructor

constructor(options?: PinchGestureHandlerOptions)

捏合手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**


| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [PinchGestureHandlerOptions](#pinchgesturehandleroptions) | 否   | 捏合手势处理器配置参数。 |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): PinchGestureHandler

设置捏合手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 捏合手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | 返回当前捏合手势处理器对象。 |

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): PinchGestureHandler

设置捏合手势处理器更新回调。捏合手势处理器移动过程中触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 捏合手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | 返回当前捏合手势处理器对象。 |

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): PinchGestureHandler

设置捏合手势处理器结束回调。捏合手势处理器识别成功后，手指抬起时触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 捏合手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | 返回当前捏合手势处理器对象。 |

### onActionCancel

onActionCancel(event: Callback\<void>): PinchGestureHandler

设置捏合手势处理器取消回调。捏合手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | 是 | 捏合手势处理器取消回调。不返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | 返回当前捏合手势处理器对象。 |

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): PinchGestureHandler

设置捏合手势处理器取消回调。捏合手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](#onactioncancel-2)接口相比，此接口返回手势事件信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 捏合手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | 返回当前捏合手势处理器对象。 |

## PinchGestureHandlerOptions

捏合手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                               | 只读   | 可选 | 说明                 |
| ------------ | ----------------------------------|---- | ---- | -------------------- |
| fingers | number | 否 | 是 | 触发捏合的最少手指数,&nbsp;最小为2指，最大为5指。<br/>默认值：2 <br/>取值范围：[2, 5]<br/>触发手势手指可以多于fingers数目，但只有先落下的与fingers相同数目的手指参与手势计算。 |
| distance | number | 否 | 是 | 最小识别距离，单位为vp。<br/>默认值：5 <br/>**说明：** <br/> 当识别距离的值小于等于0时，会被转化为默认值。|
| isFingerCountLimited<sup>15+</sup> | boolean | 否 | 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。若触摸屏幕的手指数量不等于设置的触发捏合的最少手指数（即上述fingers参数），手势将不会被识别。只有当触摸屏幕的手指数等于设置的触发捏合手势的最小手指数，并且滑动距离满足阈值要求时，手势才能被成功识别（只有先落下的两根手指参与手势计算，若抬起其中的一个，手势识别失败）。对于已经成功识别的手势，后续改变触摸屏幕的手指数量，将不会触发[onActionUpdate](ts-basic-gestures-pinchgesture.md#事件)事件，但可以触发[onActionEnd](ts-basic-gestures-pinchgesture.md#事件)事件。<br>默认值：false<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## RotationGestureHandler

旋转手势处理器对象类型。

### constructor

constructor(options?: RotationGestureHandlerOptions)

旋转手势处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**


| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [RotationGestureHandlerOptions](#rotationgesturehandleroptions) | 否   | 旋转手势处理器配置参数。 |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): RotationGestureHandler

设置旋转手势处理器识别成功回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 旋转手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | 返回当前旋转手势处理器对象。 |

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): RotationGestureHandler

设置旋转手势处理器更新回调。旋转手势处理器移动过程中触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 旋转手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | 返回当前旋转手势处理器对象。 |

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): RotationGestureHandler

设置旋转手势处理器结束回调。旋转手势处理器识别成功后，手指抬起时触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 旋转手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | 返回当前旋转手势处理器对象。 |

### onActionCancel

onActionCancel(event: Callback\<void>): RotationGestureHandler

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | 是 | 旋转手势处理器取消回调。不返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | 返回当前旋转手势处理器对象。 |

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): RotationGestureHandler

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。与[onActionCancel](#onactioncancel-3)相比，此接口返回手势事件信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent对象说明)> | 是 | 旋转手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | 返回当前旋转手势处理器对象。 |

## RotationGestureHandlerOptions

旋转手势处理器配置参数。继承自[BaseHandlerOptions](#basehandleroptions15)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                                |只读   |可选 | 说明                 |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | 否 | 是 | 触发旋转的最少手指数,&nbsp;最小为2指，最大为5指。<br/>默认值：2 <br/>取值范围：[2, 5]<br/>触发手势时手指数量可以多于fingers参数值，但仅最先落下的两指参与手势计算。|
| angle | number | 否 | 是 | 触发旋转手势的最小改变度数，单位为deg。<br/>默认值：1 <br/>**说明：** <br/>当改变度数的值小于等于0或大于360时，会被转化为默认值。|
| isFingerCountLimited<sup>15+</sup> | boolean | 否 | 是 | 是否检查触摸屏幕的手指数量。true表示检查触摸屏幕的手指数量，false表示不检查触摸屏幕的手指数量。若触摸屏幕的手指数量不等于设置的触发旋转的最少手指数（即上述fingers参数），手势将不会被识别。只有当触摸屏幕的手指数等于设置的触发旋转的最少手指数，并且滑动距离达到阈值时，手势才能被成功识别（只有先落下的两根手指参与手势计算，若抬起其中的一个，手势识别失败）。<br>对于已成功识别的手势，后续改变触摸屏幕的手指数量，不会触发[onActionUpdate](ts-basic-gestures-rotationgesture.md#事件)事件，但可以触发[onActionEnd](ts-basic-gestures-rotationgesture.md#事件)事件。<br>默认值：false<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## GestureGroupHandler

手势组处理器对象类型。

### constructor

constructor(options?: GestureGroupGestureHandlerOptions)

手势组处理器的构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [GestureGroupGestureHandlerOptions](#gesturegroupgesturehandleroptions) | 否   | 手势组处理器配置参数。 |

### onCancel

onCancel(event: Callback\<void>): GestureGroupHandler

设置手势组处理器取消回调。顺序组合手势（[GestureMode](./ts-combined-gestures.md#gesturemode枚举说明).Sequence）取消后触发回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                              | 必填 | 说明                 |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | 是 | 手势组处理器取消回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [GestureGroupHandler](#gesturegrouphandler) | 返回当前手势组处理器对象。 |

## GestureGroupGestureHandlerOptions

手势组处理器配置参数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型                               | 只读    | 可选 | 说明                 |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| mode    | [GestureMode](./ts-combined-gestures.md#gesturemode枚举说明)                        | 否 | 否   | 设置组合手势识别模式。<br/>默认值：GestureMode.Sequence      |
| gestures | [GestureHandler](#gesturehandlert)\<[TapGestureHandler](#tapgesturehandler) \| [LongPressGestureHandler](#longpressgesturehandler) \| [PanGestureHandler](#pangesturehandler) \| [SwipeGestureHandler](#swipegesturehandler) \| [PinchGestureHandler](#pinchgesturehandler) \| [RotationGestureHandler](#rotationgesturehandler) \| [GestureGroupHandler](#gesturegrouphandler)>[] | 否 | 否   | 手势组下需要包含的手势。<br/>**说明：**  <br/>当需要为一个组件同时添加单击和双击手势时，可在组合手势中添加两个TapGesture，需要双击手势在前，单击手势在后，否则不生效。 |

## GesturePriority枚举说明

绑定手势的优先级。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 |  说明 |
| ------| -- | -------- |
| NORMAL | 0 | 普通优先级手势。 |
| PRIORITY | 1 | 高优先级手势。|