# SearchOptions

Search初始化参数。

> **说明：**
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## controller

```TypeScript
controller?: SearchController
```

设置Search组件控制器。当需要通过控制器操作搜索框（如设置光标位置、停止编辑等）时传入此参数，不传入时无法使用控制器相关方法。

**类型：** [SearchController](arkts-arkui-searchcontroller-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string
```

设置搜索图标路径，默认使用系统搜索图标。  
**说明：**icon的数据源支持使用相对路径显示图片和网络图片。
- 支持的图片格式包括png、jpg、bmp、svg、gif、pixelmap和heif。
- 支持Base64字符串。格式data:image/[png|jpeg|bmp|webp|heif];base64,[base64 data], 其中[base64 data]为Base64字符串数据。
如果与属性searchIcon同时设置，则searchIcon优先。Wearable设备上默认图标大小为16vp。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

设置无输入时的提示文本。当需要自定义提示文本时传入此参数，不传入时不显示提示文本。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: string | Bindable<string>
```

Text input in the search text box.

**类型：** string \| Bindable&lt;string&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
