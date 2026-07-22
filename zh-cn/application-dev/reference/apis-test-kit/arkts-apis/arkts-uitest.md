# @ohos.UiTest

The static builder for building {@link On}object conveniently,usage example:ON.text('txt').enabled(true).

## 导入模块

```TypeScript
import { ResizeDirection, WindowMode, PenMode, PenKeyOperation, Driver, MatchPattern, UiDirection, TouchOptions, ComponentEventType, PointerMatrix, WindowChangeType, Component, ON, PenKey, Rect, InputTextMode, UIEventObserver, WindowFilter, WindowChangeOptions, UiWindow, TouchPadSwipeOptions, Point, KeyOptions, DisplayRotation, UIElementInfo, PenKeyOperationOptions, ComponentEventOptions, MouseButton, On } from '@kit.TestKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [By](arkts-test-uitest-by-c.md) | UiTest框架通过By类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。  By提供的API能力具有以下几个特点:  1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。  2、控件属性支持多种匹配模式。  3、支持控件绝对定位，相对定位，可通过[By.isBefore<sup>(deprecated)</sup>](arkts-test-uitest-by-c.md#isbefore)和[By.isAfter<sup>(deprecated)</sup>](arkts-test-uitest-by-c.md#isafter)等API限定邻近控件特征进行辅助定位。  By类提供的所有API均为同步接口，建议使用者通过静态构造器BY来链式创建By对象。 |
| [Component](arkts-test-uitest-component-c.md) | UiTest框架在API9中，Component类代表了UI界面上的一个控件，提供控件属性获取，控件点击，滑动查找，文本注入等API。该类提供的所有方法都使用Promise方式作为异步方法，需使用await调用。 |
| [Driver](arkts-test-uitest-driver-c.md) | Driver类为uitest测试框架的总入口，提供控件匹配/查找，按键注入，坐标点击/滑动，截图等能力。该类提供的方法除Driver.create()和Driver.createUIEventObserver()以外的所有方法都使用Promise方式作为异步方法，需使用await方式调用。 |
| [On](arkts-test-uitest-on-c.md) | UiTest框架从API version 9开始，通过On类提供了丰富的控件特征描述API，用于进行控件筛选来匹配/查找出目标控件。  On提供的API能力具有以下几个特点:  1、支持单属性匹配和多属性组合匹配，例如同时指定目标控件text和id。  2、控件属性支持多种匹配模式。  3、支持控件绝对定位，相对定位，可通过[ON.isBefore](arkts-test-uitest-on-c.md#isbefore)和[ON.isAfter](arkts-test-uitest-on-c.md#isafter)等API限定邻近控件特征进行辅助定位。  On类提供的所有API均为同步接口，建议使用者通过静态构造器ON来链式创建On对象。 |
| [PointerMatrix](arkts-test-uitest-pointermatrix-c.md) | 存储多指操作中每根手指每一步动作的坐标点及其行为的二维数组。 |
| [UiComponent](arkts-test-uitest-uicomponent-c.md) | UiTest中，UiComponent类代表了UI界面上的一个控件，提供控件属性获取，控件点击，滑动查找，文本注入等API。该类提供的所有方法都使用Promise方式作为异步方法，需使用await调用。 |
| [UiDriver](arkts-test-uitest-uidriver-c.md) | UiDriver类为uitest测试框架的总入口，提供控件匹配/查找，按键注入，坐标点击/滑动，截图等API。该类提供的方法除UiDriver.create()以外的所有方法都使用Promise方式作为异步方法，需使用await调用。 |
| [UiWindow](arkts-test-uitest-uiwindow-c.md) | UiWindow代表了UI界面上的一个窗口，提供窗口属性获取，窗口拖动、调整窗口大小等能力。该类提供的所有方法都使用Promise方式作为异步方法，需使用await方式调用。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComponentEventOptions](arkts-test-uitest-componenteventoptions-i.md) | 控件操作事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。 |
| [InputTextMode](arkts-test-uitest-inputtextmode-i.md) | 输入文本的方式。 |
| [KeyOptions](arkts-test-uitest-keyoptions-i.md) | 表示按键操作的选项。 |
| [PenKeyOperationOptions](arkts-test-uitest-penkeyoperationoptions-i.md) | 笔按键操作选项。 |
| [Point](arkts-test-uitest-point-i.md) | 坐标点信息。 |
| [Rect](arkts-test-uitest-rect-i.md) | 控件的边框信息。 |
| [TouchOptions](arkts-test-uitest-touchoptions-i.md) | 触摸操作的通用选项。 |
| [TouchPadSwipeOptions](arkts-test-uitest-touchpadswipeoptions-i.md) | 触摸板多指滑动手势选项相关信息。 |
| [UIElementInfo](arkts-test-uitest-uielementinfo-i.md) | UI事件的相关信息。 |
| [UIEventObserver](arkts-test-uitest-uieventobserver-i.md) | UI事件监听器。 |
| [WindowChangeOptions](arkts-test-uitest-windowchangeoptions-i.md) | 窗口变化事件监听的扩展配置，用于指定监听过程配置及事件筛选条件。 |
| [WindowFilter](arkts-test-uitest-windowfilter-i.md) | 窗口的标志属性信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ComponentEventType](arkts-test-uitest-componenteventtype-e.md) | 支持监听的控件操作事件类型。 |
| [DisplayRotation](arkts-test-uitest-displayrotation-e.md) | 设备显示器的显示方向。 |
| [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 控件属性支持的匹配模式。 |
| [MouseButton](arkts-test-uitest-mousebutton-e.md) | 模拟注入的鼠标按钮。 |
| [PenKey](arkts-test-uitest-penkey-e.md) | 笔按键类型枚举。 |
| [PenKeyOperation](arkts-test-uitest-penkeyoperation-e.md) | 笔按键操作类型枚举。 |
| [PenMode](arkts-test-uitest-penmode-e.md) | 笔模式枚举。 |
| [ResizeDirection](arkts-test-uitest-resizedirection-e.md) | 窗口调整大小的方向。 |
| [UiDirection](arkts-test-uitest-uidirection-e.md) | 进行抛滑等UI操作时的方向。 |
| [WindowChangeType](arkts-test-uitest-windowchangetype-e.md) | 支持监听的窗口变化事件类型。 |
| [WindowMode](arkts-test-uitest-windowmode-e.md) | 窗口的窗口模式。 |

