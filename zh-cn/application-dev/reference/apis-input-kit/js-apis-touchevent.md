# @ohos.multimodalInput.touchEvent (触屏输入事件)

设备上报的触屏事件，继承自[InputEvent](./js-apis-inputevent.md)。

> **说明：**
>
>- 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>- 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { Action,ToolType,SourceType,Touch,TouchEvent } from '@kit.InputKit';
```

## Action

触屏事件类型。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称     | 值   | 说明   |
| ------ | ------ | ---- |
| CANCEL | 0 | 触屏取消。 |
| DOWN   | 1 | 触屏按下。 |
| MOVE   | 2 | 触屏移动。 |
| UP     | 3 | 触屏抬起。 |

## ToolType

操作触屏的工具类型。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称       | 值   | 说明   |
| -------- | ------ | ---- |
| FINGER   | 0 | 手指。  |
| PEN      | 1 | 笔。    |
| RUBBER   | 2 | 橡皮擦。  |
| BRUSH    | 3 | 笔刷。   |
| PENCIL   | 4 | 铅笔。   |
| AIRBRUSH | 5 | 气笔。   |
| MOUSE    | 6 | 鼠标。   |
| LENS     | 7 | 透镜。   |

## SourceType 

触屏来源的设备类型，当前仅支持触摸屏、触控板类型上报。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称           | 值  | 说明   |
| ------------ | ------ | ---- |
| TOUCH_SCREEN | 0 | 触摸屏。  |
| PEN          | 1 | 手写笔。  |
| TOUCH_PAD    | 2 | 触控板。  |

## Touch

触屏点信息。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称          | 类型   | 只读   | 可选   | 说明                                  |
| ----------- | ------ | ---- | ---- | ----------------------------------- |
| id          | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏事件标识。                                |
| pressedTime | ArkTS-Dyn: number<br/>ArkTS-Sta: long | 否    | 否    | 按下时间戳，单位：μs。                           |
| screenX     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏位置所属的屏幕x坐标。                        |
| screenY     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏位置所属的屏幕y坐标。                        |
| windowX     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏位置在窗口中的x坐标。                        |
| windowY     | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏位置在窗口中的y坐标。                        |
| pressure    | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 否    | 否    | 压力值，取值范围是[0.0, 1.0]，0.0表示不支持。       |
| width       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏区域的宽度。                           |
| height      | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 触屏区域的高度。                           |
| tiltX       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 相对YZ平面的角度，取值的范围[-90, 90]，其中正值是向右倾斜。 |
| tiltY       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 相对XZ平面的角度，取值的范围[-90, 90]，其中正值是向下倾斜。 |
| toolX       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 工具区域的中心点x坐标。                           |
| toolY       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 工具区域的中心点y坐标。                           |
| toolWidth   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 工具区域宽度。                              |
| toolHeight  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 工具区域高度。                              |
| rawX        | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 输入设备上的x坐标。                          |
| rawY        | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否    | 否    | 输入设备上的y坐标。                           |
| toolType    | [ToolType](#tooltype) | 否    | 否    | 工具类型。                                |

## TouchEvent

触屏事件。

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：22

| 名称         | 类型       | 只读   | 可选   | 说明        |
| ---------- | ---------- | ---- | ---- | --------- |
| action     | [Action](#action)     | 否    | 否    | 触屏事件类型。     |
| touch      | [Touch](#touch)      | 否    | 否    | 当前触屏点信息。   |
| touches    | [Touch](#touch)[]    | 否    | 否    | 所有触屏点。     |
| sourceType | [SourceType](#sourcetype) | 否    | 否    | 触屏来源的设备类型。 |
| isInject<sup>20+</sup>   | boolean     | 否   | 是    | 是否注入事件。<br>**ArkTS-Dyn起始版本**：20 <br>**ArkTS-Sta起始版本**：22  |

