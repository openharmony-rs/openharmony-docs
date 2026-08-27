# SwipeRefresher

内容加载指获取内容并加载出来，常用于衔接展示下拉加载的内容。

> **说明：**
> 
> - 该组件及其子组件从 API version 10 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果SwipeRefresher设置通用属性和通用事件，编
> 译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到SwipeRefresher本身。
> 这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议SwipeRefresher设置通用属性和通用事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SwipeRefresher } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

内容加载时显示的文本。默认值：空字符串。  
**说明：**如果文本大于列宽时，文本被截断。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isLoading

```TypeScript
isLoading: boolean
```

当前是否正在加载。true：正在加载。false：未在加载。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
