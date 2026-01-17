# @ohos.multimodalInput.gestureEvent (手势事件)

设备上报的手势事件。

>  **说明：**
>
>- 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>- 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { Rotate, Pinch, ThreeFingersSwipe, FourFingersSwipe, ActionType, SwipeInward } from '@kit.InputKit';
```

## Pinch

捏合事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

| 名称             | 类型        | 只读   | 可选   | 说明                                       |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | 否    | 否    | 捏合事件类型。                                   |
| scale        |  ArkTS-Dyn: number<br/>ArkTS-Sta: double      | 否    | 否    | 捏合度，取值范围大于等于0。                             |

## Rotate<sup>11+</sup>

旋转事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称             | 类型        | 只读   | 可选   | 说明                                       |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type | [ActionType](#actiontype)   | 否    | 否    | 旋转事件类型。                                   |
| angle | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否    | 否    | 旋转角度。                             |

## ThreeFingersSwipe

三指滑动事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

| 名称             | 类型        | 只读   | 可选   | 说明                                       |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | 否    | 否    | 三指滑动事件类型。                                   |
| x        | ArkTS-Dyn: number<br/>ArkTS-Sta: int      | 否    | 否    | 坐标x。                             |
| y        | ArkTS-Dyn: number<br/>ArkTS-Sta: int      | 否    | 否    | 坐标y。                             |

## FourFingersSwipe

四指滑动事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

| 名称             | 类型        | 只读   | 可选   | 说明                                       |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | 否    | 否    | 四指滑动事件类型。                                   |
| x        | ArkTS-Dyn: number<br/>ArkTS-Sta: int      | 否    | 否    | 坐标x。                             |
| y        | ArkTS-Dyn: number<br/>ArkTS-Sta: int      | 否    | 否    | 坐标y。                             |

## ThreeFingersTap<sup>11+</sup>

三指轻点事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称               | 类型                      | 只读 | 可选 | 说明             |
| ------------------ | ------------------------- | ---- | ---- | ---------------- |
| type | [ActionType](#actiontype) | 否   | 否   | 三指轻点事件类型。 |

## ActionType

手势事件类型。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：11

**ArkTS-Sta起始版本**：23

| 名称        | 值  | 说明             |
| ----------- | --- | --------------- |
| CANCEL      | 0   | 取消。             |
| BEGIN       | 1   | 手势开始。         |
| UPDATE      | 2   | 手势更新。         |
| END         | 3   | 手势结束。         |

## SwipeInward<sup>12+</sup>

向内滑动事件。

**系统能力**：SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：12

**ArkTS-Sta起始版本**：23

| 名称        | 类型  | 说明             |
| ----------- | --- | --------------- |
| type      | ActionType   |        表示向内滑动事件的类型，固定为 SwipeInward。     |
| x       | ArkTS-Dyn: number<br/>ArkTS-Sta: int   |    滑动事件触发点的横坐标，单位为像素。      |
| y      | ArkTS-Dyn: number<br/>ArkTS-Sta: int   |     滑动事件触发点的纵坐标，单位为像素。     |