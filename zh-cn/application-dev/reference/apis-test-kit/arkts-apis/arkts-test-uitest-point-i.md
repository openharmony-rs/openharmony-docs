# Point

坐标点信息。

**起始版本：** 9

**系统能力：** SystemCapability.Test.UiTest

## 导入模块

```TypeScript
import { UiComponent, UiDriver, BY, By } from '@kit.TestKit';
```

## displayId

```TypeScript
displayId?: number
```

坐标点所属的屏幕ID，取值范围：大于等于0的整数。默认值为设备默认屏幕ID。从API version 20开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## x

```TypeScript
x: number
```

坐标点的横坐标，取值大于等于0的整数，单位：px。  
**说明：** 从API version 20开始，该属性不再为只读属性。从API version 11开始，该接口支持在原子化服务中使用。@readonly [since 9-19]

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## y

```TypeScript
y: number
```

坐标点的纵坐标，取值大于等于0的整数，单位：px。  
**说明：** 从API version 20开始，该属性不再为只读属性。从API version 11开始，该接口支持在原子化服务中使用。@readonly [since 9-19]

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.UiTest
