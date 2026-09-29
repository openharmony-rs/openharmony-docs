# FormInfo

```TypeScript
interface FormInfo
```

Widget information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [FormInfo](arkts-form-forminfo-forminfo-i.md)

<!--Device-formInfo-interface FormInfo--><!--Device-formInfo-interface FormInfo-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
```

## abilityName

```TypeScript
abilityName: string
```

Name of the ability to which the widget belongs.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [abilityName](arkts-form-forminfo-forminfo-i.md#abilityname)

<!--Device-FormInfo-abilityName: string--><!--Device-FormInfo-abilityName: string-End-->

**System capability:** SystemCapability.Ability.Form

## bundleName

```TypeScript
bundleName: string
```

Name of the bundle to which the widget belongs.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [bundleName](arkts-form-forminfo-forminfo-i.md#bundlename)

<!--Device-FormInfo-bundleName: string--><!--Device-FormInfo-bundleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## colorMode

```TypeScript
colorMode: ColorMode
```

Color mode of the widget.

**Type:** ColorMode

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [colorMode](arkts-form-forminfo-forminfo-i.md#colormode)

<!--Device-FormInfo-colorMode: ColorMode--><!--Device-FormInfo-colorMode: ColorMode-End-->

**System capability:** SystemCapability.Ability.Form

## customizeData

```TypeScript
customizeData: { [key: string]: [value: string] }
```

Custom data of the widget.

**Type:** { [key: string]: [value: string] }

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [customizeData](arkts-form-forminfo-forminfo-i.md#customizedata)

<!--Device-FormInfo-customizeData: { [key: string]: [value: string] }--><!--Device-FormInfo-customizeData: { [key: string]: [value: string] }-End-->

**System capability:** SystemCapability.Ability.Form

## defaultDimension

```TypeScript
defaultDimension: number
```

Default dimension of the widget.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [defaultDimension](arkts-form-forminfo-forminfo-i.md#defaultdimension)

<!--Device-FormInfo-defaultDimension: number--><!--Device-FormInfo-defaultDimension: number-End-->

**System capability:** SystemCapability.Ability.Form

## description

```TypeScript
description: string
```

Description of the widget.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [description](arkts-form-forminfo-forminfo-i.md#description)

<!--Device-FormInfo-description: string--><!--Device-FormInfo-description: string-End-->

**System capability:** SystemCapability.Ability.Form

## formConfigAbility

```TypeScript
formConfigAbility: string
```

Configuration ability of the widget.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [formConfigAbility](arkts-form-forminfo-forminfo-i.md#formconfigability)

<!--Device-FormInfo-formConfigAbility: string--><!--Device-FormInfo-formConfigAbility: string-End-->

**System capability:** SystemCapability.Ability.Form

## formVisibleNotify

```TypeScript
formVisibleNotify: boolean
```

Whether to send a notification when the widget is visible.

- **true**: The widget provider is notified of the status change.  
- **false**: The widget provider is not notified of the status change.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [formVisibleNotify](arkts-form-forminfo-forminfo-i.md#formvisiblenotify)

<!--Device-FormInfo-formVisibleNotify: boolean--><!--Device-FormInfo-formVisibleNotify: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## isDefault

```TypeScript
isDefault: boolean
```

Whether the widget is the default one.

- **true**: The widget is the default one.  
- **false**: The widget is not the default one.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDefault](arkts-form-forminfo-forminfo-i.md#isdefault)

<!--Device-FormInfo-isDefault: boolean--><!--Device-FormInfo-isDefault: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## jsComponentName

```TypeScript
jsComponentName: string
```

Component name of the JS widget.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [jsComponentName](arkts-form-forminfo-forminfo-i.md#jscomponentname)

<!--Device-FormInfo-jsComponentName: string--><!--Device-FormInfo-jsComponentName: string-End-->

**System capability:** SystemCapability.Ability.Form

## moduleName

```TypeScript
moduleName: string
```

Name of the module to which the widget belongs.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [moduleName](arkts-form-forminfo-forminfo-i.md#modulename)

<!--Device-FormInfo-moduleName: string--><!--Device-FormInfo-moduleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## name

```TypeScript
name: string
```

Widget name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [name](arkts-form-forminfo-forminfo-i.md#name)

<!--Device-FormInfo-name: string--><!--Device-FormInfo-name: string-End-->

**System capability:** SystemCapability.Ability.Form

## relatedBundleName

```TypeScript
relatedBundleName: string
```

Name of the associated bundle to which the widget belongs.

**Type:** string

**Since:** 8

**Deprecated since:** 9

<!--Device-FormInfo-relatedBundleName: string--><!--Device-FormInfo-relatedBundleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## scheduledUpdateTime

```TypeScript
scheduledUpdateTime: string
```

Time when the widget was updated.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [scheduledUpdateTime](arkts-form-forminfo-forminfo-i.md#scheduledupdatetime)

<!--Device-FormInfo-scheduledUpdateTime: string--><!--Device-FormInfo-scheduledUpdateTime: string-End-->

**System capability:** SystemCapability.Ability.Form

## supportDimensions

```TypeScript
supportDimensions: Array<number>
```

Dimensions supported by the widget.

**Type:** Array&lt;number&gt;

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [supportDimensions](arkts-form-forminfo-forminfo-i.md#supportdimensions)

<!--Device-FormInfo-supportDimensions: Array<number>--><!--Device-FormInfo-supportDimensions: Array<number>-End-->

**System capability:** SystemCapability.Ability.Form

## type

```TypeScript
type: FormType
```

Type of the widget. Currently, only JS widgets are supported.

**Type:** FormType

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [type](arkts-form-forminfo-forminfo-i.md#type)

<!--Device-FormInfo-type: FormType--><!--Device-FormInfo-type: FormType-End-->

**System capability:** SystemCapability.Ability.Form

## updateDuration

```TypeScript
updateDuration: number
```

Update period of the widget.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateDuration](arkts-form-forminfo-forminfo-i.md#updateduration)

<!--Device-FormInfo-updateDuration: number--><!--Device-FormInfo-updateDuration: number-End-->

**System capability:** SystemCapability.Ability.Form

## updateEnabled

```TypeScript
updateEnabled: boolean
```

Whether the widget is updatable.

- **true**: The widget can be updated periodically.  
- **false**: The widget cannot be updated periodically.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateEnabled](arkts-form-forminfo-forminfo-i.md#updateenabled)

<!--Device-FormInfo-updateEnabled: boolean--><!--Device-FormInfo-updateEnabled: boolean-End-->

**System capability:** SystemCapability.Ability.Form
