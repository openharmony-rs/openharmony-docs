# InputMethodSubtype

**@ohos.InputMethodSubtype**模块提供输入法子类型的属性数据定义，支持描述输入法在不同语言或模式下的子类型信息。

本模块是输入法框架的子类型数据模块，定义了`InputMethodSubtype`接口，用于描述输入法的一种具体输入模式或语言——如中文键盘、英文键盘、大写模式键盘等，每个子类型代表输入法在特定语言或模式下的形态。

本模块提供输入法子类型的属性描述能力。通过`InputMethodSubtype`可获取子类型的标识（`id`、`name`）、语言和区域（`locale`、`language`）、显示标签（`label`）、模式（`mode`：大写
/小写）、图标等属性，用于输入法子类型的识别、展示和切换。

当需要查询、展示或切换输入法的不同语言/模式子类型时使用本模块。典型场景包括：系统设置应用展示输入法子类型列表供用户选择、输入法应用根据子类型信息切换语言或模式、应用获取当前输入法子类型信息等。

`InputMethodSubtype`是纯数据定义模块，其对象由系统框架创建和返回，开发者不可自行构造。典型跨模块使用流程：

1. **编辑框应用侧**（`@ohos.inputMethod`模块）：通过`InputMethodSetting.listInputMethodSubtype()`查询输入法子类型列表，通过`inputMethod.switchCurrentInputMethodSubtype()`切换到指定子类型。
2. **输入法应用侧**（`@ohos.inputMethodEngine`模块）：通过`InputMethodAbility.on('setSubtype')`监听子类型切换事件，回调参数为`InputMethodSubtype`对象，据此调整键盘布局和语言。

本模块的核心开放能力由以下关键接口承载：

本模块为纯数据定义模块，`InputMethodSubtype`作为子类型描述数据需与其他模块的API组合使用。典型组合场景为：在`@ohos.inputMethod`模块中，通过`InputMethodSetting`查询和切换子类
型；在`@ohos.inputMethodEngine`模块中，通过`InputMethodAbility`监听子类型切换事件。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## extra

```TypeScript
extra?: object
```

输入法子类型的其他信息。

**类型：** object

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
readonly icon?: string
```

输入法子类型的图标，可以通过iconId查询获取。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## iconId

```TypeScript
readonly iconId?: number
```

输入法子类型的图标id。用于通过资源ID加载子类型图标。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## id

```TypeScript
readonly id: string
```

输入法子类型的id。与输入法应用在module.json5中配置的subtype id保持一致，用于在同输入法应用内唯一标识一个子类型。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## label

```TypeScript
readonly label?: string
```

输入法子类型的标签。用于在UI界面展示子类型的名称，如"中文（简体）"、"English"等。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## labelId

```TypeScript
readonly labelId?: number
```

输入法子类型的标签资源号。用于通过资源ID加载标签文本，支持多语言场景下的标签国际化显示。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## language

```TypeScript
readonly language: string
```

输入法子类型的语言，如'zh'（中文）、'en'（英文）。用于标识子类型的语言，是locale的子集。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## locale

```TypeScript
readonly locale: string
```

输入法子类型的区域。遵循ICU Locale格式，如'zh-CN'表示中文（简体，中国）、'en-US'表示英文（美国）。用于标识子类型的语言和地区。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## mode

```TypeScript
readonly mode?: 'upper' | 'lower'
```

输入法子类型的模式，包括upper（大写）和lower（小写）。用于描述键盘的大小写状态模式。

**类型：** 'upper' | 'lower'

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
readonly name: string
```

输入法子类型所属应用的包名。与输入法应用在module.json5中配置的bundleName保持一致，用于标识该子类型属于哪个输入法应用。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

