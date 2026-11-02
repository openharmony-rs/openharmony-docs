# 设置组件绑定的手势
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

用于设置组件绑定的手势。可以通过UIGestureEvent对象动态添加、删除或清除组件上的手势，支持配置手势优先级、事件响应设置以及与子组件手势同时触发的并行手势，适用于运行时管理组件手势交互的场景。

>**说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 在[GestureEvent](ts-gesture-common.md#gestureevent对象说明)的fingerList元素中，手指索引编号与位置相对应，即fingerList[index]的id为index。对于先按下但未参与当前手势触发的手指，fingerList中对应的位置为undefined。建议优先使用fingerInfos。

## UIGestureEvent

用于设置组件绑定的手势。

### addGesture

ArkTS-Dyn: addGesture\<T>(gesture: GestureHandler\<T>, priority?: GesturePriority, mask?: GestureMask): void

ArkTS-Sta: addGesture(gesture: GestureHandler, priority?: GesturePriority, mask?: GestureMask): void

添加手势。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| gesture  |  ArkTS-Dyn: [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert)<br/>ArkTS-Sta: [GestureHandler](./ts-gesturehandler.md#gesturehandler23) | 是   | 手势处理器对象。 |
| priority  |  [GesturePriority](./ts-gesturehandler.md#gesturepriority枚举说明) | 否   | 绑定手势的优先级。<br>默认值：GesturePriority.NORMAL |
| mask  |  [GestureMask](./ts-gesture-common.md#gesturemask枚举说明) | 否   | 事件响应设置。<br>默认值：GestureMask.Normal |

### addParallelGesture

ArkTS-Dyn: addParallelGesture\<T>(gesture: GestureHandler\<T>, mask?: GestureMask): void

ArkTS-Sta: addParallelGesture(gesture: GestureHandler, mask?: GestureMask): void

绑定可与子组件手势同时触发的手势。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| gesture  |  ArkTS-Dyn: [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert)<br/>ArkTS-Sta: [GestureHandler](./ts-gesturehandler.md#gesturehandler23) | 是   | 手势处理器对象。 |
| mask  |  [GestureMask](./ts-gesture-common.md#gesturemask枚举说明) | 否   | 事件响应设置。<br>默认值：GestureMask.Normal |

### removeGestureByTag

removeGestureByTag(tag: string): void

移除该组件上通过modifier绑定且设置了指定标志的手势。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| tag  |  string | 是   | 要移除的手势处理器标志，用于匹配并移除当前组件上通过 modifier 绑定且设置了该标志的手势。 |

### clearGestures

clearGestures(): void

清除该组件上通过modifier绑定的所有手势，适用于组件交互模式切换或需要禁用全部动态手势的场景。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

## 示例

见[动态手势设置](./ts-universal-attributes-gesture-modifier.md)。