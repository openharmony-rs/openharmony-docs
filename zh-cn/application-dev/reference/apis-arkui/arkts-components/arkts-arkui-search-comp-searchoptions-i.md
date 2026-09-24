# SearchOptions

```TypeScript
declare interface SearchOptions
```

Search初始化参数。

> **说明：** 
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

设置Search组件控制器。当需要通过控制器操作搜索框（如设置光标位置、停止编辑等）时传入此参数，不传入时无法使用控制器相关方法。

**类型：** [SearchController](arkts-arkui-search-comp-searchcontroller-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string
```

设置搜索图标路径，默认使用系统搜索图标。

**说明：** 

icon的数据源支持[使用相对路径显示图片](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#示例25使用相对路径显示图片)和网络图片。

- 支持的图片格式包括png、jpg、bmp、svg、gif、pixelmap和heif。

- 支持Base64字符串。格式data:image/[png|jpeg|bmp|webp|heif];base64,[base64 data], 其中[base64 data]为Base64字符串数据。

如果与属性searchIcon同时设置，则searchIcon优先。

Wearable设备上默认图标大小为16vp。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。当需要自定义提示文本时传入此参数，不传入时不显示提示文本。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

设置当前显示的搜索文本内容。当需要设置搜索框的初始文本内容时传入此参数，不传入时搜索框为空。

从API version 10开始，该参数支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
