# KeyOptions

```TypeScript
declare interface KeyOptions
```

按键操作选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface KeyOptions--><!--Device-unnamed-declare interface KeyOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## 导入模块

```TypeScript
import { Component, DisplayRotation, Driver, MatchPattern, MouseButton, ON, On, PointerMatrix, ResizeDirection, UIElementInfo, UIEventObserver, UiDirection, UiWindow, WindowMode, Point, WindowFilter, Rect, TouchPadSwipeOptions, InputTextMode, WindowChangeType, ComponentEventType, WindowChangeOptions, ComponentEventOptions, TouchOptions, KeyOptions, PenKey, PenMode, PenKeyOperation, PenKeyOperationOptions } from '@kit.TestKit';
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## key1

```TypeScript
key1?: number
```

操作时注入的第一个按键值，取值范围：[KeyCode键码值](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md)。未设置时不注入按键事件。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-KeyOptions-key1?: int--><!--Device-KeyOptions-key1?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## key2

```TypeScript
key2?: number
```

操作时注入的第二个按键值，取值范围：[KeyCode键码值](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keycode-keycode-e.md)。未设置时不注入按键事件。

**说明：** 仅设置key2而不设置key1时，将抛出17000007参数校验失败的错误。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-KeyOptions-key2?: int--><!--Device-KeyOptions-key2?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

**测试接口：** 此接口仅在自动化测试脚本中使用。
