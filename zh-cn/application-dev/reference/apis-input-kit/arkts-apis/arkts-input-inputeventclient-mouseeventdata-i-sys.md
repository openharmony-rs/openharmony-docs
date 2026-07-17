# MouseEventData（系统接口）

鼠标注入描述信息。

**起始版本：** 11

<!--Device-inputEventClient-interface MouseEventData--><!--Device-inputEventClient-interface MouseEventData-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## mouseEvent

```TypeScript
mouseEvent: MouseEvent
```

鼠标事件。

**类型：** MouseEvent

**起始版本：** 11

<!--Device-MouseEventData-mouseEvent: MouseEvent--><!--Device-MouseEventData-mouseEvent: MouseEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

## useGlobalCoordinate

```TypeScript
useGlobalCoordinate? : boolean
```

是否使用全局坐标来计算注入的鼠标事件。默认值为false，取值为false表示使用以指定屏幕左上角为原点的相对坐标系的坐标来计算注入的鼠标事件。取值为true表示使用以主屏左上角为原点的全局坐标系的坐标来计算注入的鼠标事件。

**类型：** boolean

**起始版本：** 20

<!--Device-MouseEventData-useGlobalCoordinate? : boolean--><!--Device-MouseEventData-useGlobalCoordinate? : boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

