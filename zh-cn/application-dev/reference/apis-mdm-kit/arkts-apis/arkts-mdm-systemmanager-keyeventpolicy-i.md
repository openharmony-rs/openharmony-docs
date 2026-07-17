# KeyEventPolicy

按键事件处理策略。按键事件发生时，仅拦截响应已下发按键事件处理策略的按键。对于未下发按键事件处理策略的按键事件，系统执行原先的响应逻辑。

**起始版本：** 23

<!--Device-systemManager-interface KeyEventPolicy--><!--Device-systemManager-interface KeyEventPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## keyCode

```TypeScript
keyCode: KeyCode
```

按键编码。

**类型：** KeyCode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEventPolicy-keyCode: KeyCode--><!--Device-KeyEventPolicy-keyCode: KeyCode-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## keyPolicy

```TypeScript
keyPolicy: KeyPolicy
```

按键策略。

**类型：** KeyPolicy

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyEventPolicy-keyPolicy: KeyPolicy--><!--Device-KeyEventPolicy-keyPolicy: KeyPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

