# UIElementInfo

UI事件的相关信息。

**起始版本：** 10

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

应用包名。从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentEventType

```TypeScript
readonly componentEventType?: ComponentEventType
```

控件操作事件类型，若非控件操作事件返回ComponentEventType.COMPONENT_UNDEFINED。从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [ComponentEventType](arkts-test-uitest-componenteventtype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentId

```TypeScript
readonly componentId?: string
```

控件id，若非控件操作事件返回空字符串。从API version 22开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentRect

```TypeScript
readonly componentRect?: Rect
```

控件边框信息，若非控件操作事件则返回属性值均为0的Rect对象。从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [Rect](arkts-test-uitest-rect-i.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## text

```TypeScript
readonly text: string
```

控件/窗口的文本信息。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.text('123'); // 使用静态构造器ON创建On对象，指定目标控件的text属性。
```

```TypeScript
// xxx.test.ets
import { BY, By } from '@kit.TestKit';

let by: By = BY.text('123'); // 使用静态构造器BY创建By对象，指定目标控件的text属性。
```

## type

```TypeScript
readonly type: string
```

控件/窗口类型。从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.type('Button'); // 使用静态构造器ON创建On对象，指定目标控件的控件类型属性。
```

```TypeScript
// xxx.test.ets
import { On, ON, MatchPattern } from '@kit.TestKit';

let on: On = ON.type('Button', MatchPattern.EQUALS); // 使用静态构造器ON创建On对象，指定目标控件的控件类型属性。
```

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.type('Button'); // 使用静态构造器BY创建By对象，指定目标控件的控件类型属性。
```

## windowChangeType

```TypeScript
readonly windowChangeType?: WindowChangeType
```

窗口变化事件类型，若非窗口变化事件返回WindowChangeType.WINDOW_UNDEFINED。从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [WindowChangeType](arkts-test-uitest-windowchangetype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## windowId

```TypeScript
readonly windowId?: number
```

控件所属窗口id。从API version 22开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest
