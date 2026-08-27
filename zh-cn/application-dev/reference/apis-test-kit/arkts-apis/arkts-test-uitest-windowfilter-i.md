# WindowFilter

窗口的标志属性信息。

**起始版本：** 9

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## active

```TypeScript
active?: boolean
```

窗口是否正与用户进行交互，true：交互状态，false：未交互状态，默认值为false。从API version 11开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## actived

```TypeScript
actived?: boolean
```

窗口是否正与用户进行交互，true：交互状态，false：未交互状态，默认值为false。从API version 11开始废弃，建议使用active替代。

**类型：** boolean

**起始版本：** 9

**废弃版本：** 11

**替代接口：** active

**系统能力：** SystemCapability.Test.UiTest

## bundleName

```TypeScript
bundleName?: string
```

窗口归属应用的包名，默认值为空，用于在多窗口场景下根据应用包名筛选目标窗口。从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## displayId

```TypeScript
displayId?: number
```

窗口所属的屏幕ID。取值大于或等于0的整数。默认值为设备默认屏幕ID。从API version 20开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## focused

```TypeScript
focused?: boolean
```

窗口是否处于获焦状态，true：获焦状态，false：未获焦状态，默认值为false。从API version 11开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

**示例**

```TypeScript
// xxx.test.ets
import { On, ON } from '@kit.TestKit';

let on: On = ON.focused(true); // 使用静态构造器ON创建On对象，指定目标控件的获焦状态属性。
```

```TypeScript
// xxx.test.ets
import { By, BY } from '@kit.TestKit';

let by: By = BY.focused(true); // 使用静态构造器BY创建By对象，指定目标控件的获焦状态属性。
```

## title

```TypeScript
title?: string
```

窗口的标题信息，默认值为空，用于在多窗口场景下根据窗口标题筛选目标窗口。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest
