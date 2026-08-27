# AtomicServiceSearch

AtomicServiceSearch为开发者提供满足定制化需求的功能，内容包括默认显示的搜索区、可自定义的选择区和功能区（最多两个）。

> **说明：**
> 
> 该组件从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## controller

```TypeScript
controller?: SearchController
```

Search组件控制器，用于设置输入光标的位置、退出编辑态等操作。默认值为undefined。

**类型：** [SearchController](../arkts-components/arkts-arkui-searchcontroller-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation?: OperationParams
```

功能区（右侧）的功能设置项。默认值为undefined。

**类型：** [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

搜索框内默认显示的提示文本。默认值为Search。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## search

```TypeScript
search?: SearchParams
```

search搜索区可支持的事件及样式。默认值为undefined。

**类型：** [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
select?: SelectParams
```

select选择区的内容、事件及样式。默认值为undefined。

**类型：** [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

设置当前显示的搜索文本内容。默认值为空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
