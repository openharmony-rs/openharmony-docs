# SearchOptions

Search初始化参数。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-declare interface SearchOptions--><!--Device-unnamed-declare interface SearchOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

Search组件的控制器。

**类型：** SearchController

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchOptions-controller?: SearchController--><!--Device-SearchOptions-controller?: SearchController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string
```

搜索图标的路径。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchOptions-icon?: string--><!--Device-SearchOptions-icon?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

无输入时显示的文本。

**类型：** ResourceStr

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SearchOptions-placeholder?: ResourceStr--><!--Device-SearchOptions-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: string | Bindable<string>
```

Text input in the search text box.

**类型：** string \| Bindable&lt;string&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SearchOptions-value?: string | Bindable<string>--><!--Device-SearchOptions-value?: string | Bindable<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

