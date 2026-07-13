# InputMethodProperty

输入法应用属性。

**起始版本：** 8

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## enabledState

```TypeScript
readonly enabledState?: EnabledState
```

非必填。

- 当InputMethodProperty用于切换、查询等接口的入参时，开发者可不填写此字段，通过name和id即可唯一指定一个输入法扩展
- 当InputMethodProperty作为查询接口的返回值时（如[getCurrentInputMethod](arkts-ime-getcurrentinputmethod-f.md#getcurrentinputmethod-1)），此字段表示该输入法启用状
态。

**类型：** EnabledState

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## extra

```TypeScript
extra?: object
```

输入法扩展信息。

- API version 10起：非必填；
- API version 9：必填。

**类型：** object

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
readonly icon?: string
```

非必填。

- 当InputMethodProperty用于切换、查询等接口的入参时，开发者可不填写此字段，通过name和id即可唯一指定一个输入法扩展。
- 当InputMethodProperty作为查询接口的返回值时（如[getCurrentInputMethod](arkts-ime-getcurrentinputmethod-f.md#getcurrentinputmethod-1)），此字段表示输入法图标数
据，可以通过iconId查询获取。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## iconId

```TypeScript
readonly iconId?: number
```

非必填。

- 当InputMethodProperty用于切换、查询等接口的入参时，开发者可不填写此字段，通过name和id即可唯一指定一个输入法扩展。
- 当InputMethodProperty作为查询接口的返回值时（如[getCurrentInputMethod](arkts-ime-getcurrentinputmethod-f.md#getcurrentinputmethod-1)），此字段表示icon字段的
资源号。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## id

```TypeScript
readonly id: string
```

必填。输入法扩展在应用内唯一标识，与name一起组成输入法扩展的全局唯一标识。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## label

```TypeScript
readonly label?: string
```

非必填。

- 当InputMethodProperty用于切换、查询等接口的入参时，开发者可不填写此字段，通过name和id即可唯一指定一个输入法扩展。
- 当InputMethodProperty作为查询接口的返回值时（如[getCurrentInputMethod](arkts-ime-getcurrentinputmethod-f.md#getcurrentinputmethod-1)），此字段表示输入法扩展对外
显示的名称，优先使用InputMethodExtensionAbility中配置的label，若未配置，自动使用应用入口ability的label；当应用入口ability未配置label时，自动使用应用AppScope中配置
的label。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## labelId

```TypeScript
readonly labelId?: number
```

非必填。

- 当InputMethodProperty用于切换、查询等接口的入参时，开发者可不填写此字段，通过name和id即可唯一指定一个输入法扩展。
- 当InputMethodProperty作为查询接口的返回值时（如[getCurrentInputMethod](arkts-ime-getcurrentinputmethod-f.md#getcurrentinputmethod-1)），此字段表示label字段
的资源号。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## methodId

```TypeScript
readonly methodId: string
```

输入法唯一标识。必填。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [id](arkts-ime-inputmethodproperty-i.md#id)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
readonly name: string
```

必填。输入法包名。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## packageName

```TypeScript
readonly packageName: string
```

输入法包名。必填。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [name](arkts-ime-inputmethodproperty-i.md#name)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

