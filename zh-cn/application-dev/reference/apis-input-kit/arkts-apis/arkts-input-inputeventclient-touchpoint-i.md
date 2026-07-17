# TouchPoint

表示屏幕上的单个触点信息。

**起始版本：** 26.0.0

<!--Device-inputEventClient-interface TouchPoint--><!--Device-inputEventClient-interface TouchPoint-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## displayId

```TypeScript
displayId: number
```

触点所在屏幕的唯一标识，必须为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchPoint-displayId: int--><!--Device-TouchPoint-displayId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## displayX

```TypeScript
displayX: number
```

触点相对于屏幕左边缘的X坐标，单位为像素（px），必须为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchPoint-displayX: int--><!--Device-TouchPoint-displayX: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## displayY

```TypeScript
displayY: number
```

触点相对于屏幕上边缘的Y坐标，单位为像素（px），必须为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchPoint-displayY: int--><!--Device-TouchPoint-displayY: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## id

```TypeScript
id: number
```

触点唯一标识。取值范围为[0, 9]，且必须为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchPoint-id: int--><!--Device-TouchPoint-id: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

