# InputMethodProperty

Describes the input method application attributes.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## enabledState

```TypeScript
readonly enabledState?: EnabledState
```

Optional. <br> <br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension. <br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates whether the input method is enabled.

**Type:** [EnabledState](arkts-ime-inputmethod-enabledstate-e.md)

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## extra

```TypeScript
extra?: object
```

Extra information about the input method. This parameter is reserved and currently has no specific meaning. <br> <br>- API version 10 and later: optional <br>- API version 9: mandatory

**Type:** object

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
readonly icon?: string
```

Optional. <br> <br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension. <br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the input method icon data, which can be obtained through icon ID.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## iconId

```TypeScript
readonly iconId?: number
```

Optional. <br> <br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension. <br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the resource ID of the **icon** field.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## id

```TypeScript
readonly id: string
```

Mandatory. Unique identifier of an input method extension in an app. **id** and **name** form a globally unique identifier of the input method extension.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## label

```TypeScript
readonly label?: string
```

Optional. <br> <br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension. <br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the name of the input method extension displayed externally. Use the label configured for the InputMethodExtensionAbility. If no label is configured, the label of the application entry ability is automatically used. If no label is configured for the application entry ability, the label configured in **AppScope** is automatically used.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## labelId

```TypeScript
readonly labelId?: number
```

Optional. <br> <br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension. <br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the resource ID of the **label** field.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## methodId

```TypeScript
readonly methodId: string
```

Unique ID of the input method. Mandatory.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](#id)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
readonly name: string
```

Mandatory. Name of the input method package.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## packageName

```TypeScript
readonly packageName: string
```

Name of the input method package. Mandatory.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [name](#name)

**System capability:** SystemCapability.MiscServices.InputMethodFramework
