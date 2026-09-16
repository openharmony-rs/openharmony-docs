# SwipeRefresher

内容加载指获取内容并加载出来，常用于衔接展示下拉加载的内容。

> **说明：** 
> 
> - 如果SwipeRefresher设置[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)或[通用事件](../arkts-components/arkts-arkui-commonmethod-c.md)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SwipeRefresher本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议SwipeRefresher设置通用属性和通用事件。

## 导入模块

```ts
import { SwipeRefresher } from '@kit.ArkUI';
```

## 子组件

无

**起始版本：** 10

**装饰器类型：** @Component

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

内容加载时显示的文本。

默认值：空字符串。

**说明：** 如果文本大于列宽时，文本被截断。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isLoading

```TypeScript
isLoading: boolean
```

当前是否正在加载。

true：正在加载。

false：未在加载。

**类型：** boolean

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
