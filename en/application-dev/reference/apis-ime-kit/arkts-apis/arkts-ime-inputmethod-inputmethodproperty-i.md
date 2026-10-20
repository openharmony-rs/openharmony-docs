# InputMethodProperty

```TypeScript
interface InputMethodProperty
```

Describes the input method application properties.

**Since:** 8

<!--Device-inputMethod-interface InputMethodProperty--><!--Device-inputMethod-interface InputMethodProperty-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## enabledState

```TypeScript
readonly enabledState?: EnabledState
```

Optional. <br> <br>- When **InputMethodProperty** is used as an input parameter of APIs such as switch and query, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**. <br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the enabled state of the input method.

**Type:** [EnabledState](arkts-ime-inputmethod-enabledstate-e.md)

**Since:** 20

<!--Device-InputMethodProperty-readonly enabledState?: EnabledState--><!--Device-InputMethodProperty-readonly enabledState?: EnabledState-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## extra

```TypeScript
extra?: object
```

Input method extension information. <br> <br>- Since API version 10: optional <br>- API version 9: mandatory

**Type:** object

**Since:** 9

<!--Device-InputMethodProperty-extra?: object--><!--Device-InputMethodProperty-extra?: object-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
readonly icon?: string
```

Optional. <br> <br>- When **InputMethodProperty** is used as an input parameter of APIs such as switch and query, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**. <br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the input method icon data, which can be obtained by querying **iconId**.

**Type:** string

**Since:** 9

<!--Device-InputMethodProperty-readonly icon?: string--><!--Device-InputMethodProperty-readonly icon?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## iconId

```TypeScript
readonly iconId?: number
```

Optional. <br> <br>- When **InputMethodProperty** is used as an input parameter of APIs such as switch and query, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**. <br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the resource ID of the **icon** field.

**Type:** number

**Since:** 9

<!--Device-InputMethodProperty-readonly iconId?: long--><!--Device-InputMethodProperty-readonly iconId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## id

```TypeScript
readonly id: string
```

Mandatory. Unique identifier of the input method extension within the application. Together with name, it forms the globally unique identifier of the input method extension.

**Type:** string

**Since:** 9

<!--Device-InputMethodProperty-readonly id: string--><!--Device-InputMethodProperty-readonly id: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## label

```TypeScript
readonly label?: string
```

Optional. <br> <br>- When **InputMethodProperty** is used as an input parameter of APIs such as switch and query, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**. <br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the display name of the input method extension. The label configured in **InputMethodExtensionAbility** is used first; if it is not configured, the label of the application entry ability is automatically used; if the application entry ability does not configure a label, the label configured in the application **AppScope** is automatically used.

**Type:** string

**Since:** 9

<!--Device-InputMethodProperty-readonly label?: string--><!--Device-InputMethodProperty-readonly label?: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## labelId

```TypeScript
readonly labelId?: number
```

Optional. <br> <br>- When **InputMethodProperty** is used as an input parameter of APIs such as switch and query, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**. <br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md)), this field indicates the resource ID of the **label** field.

**Type:** number

**Since:** 10

<!--Device-InputMethodProperty-readonly labelId?: long--><!--Device-InputMethodProperty-readonly labelId?: long-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## name

```TypeScript
readonly name: string
```

Mandatory. Input method package name.

**Type:** string

**Since:** 9

<!--Device-InputMethodProperty-readonly name: string--><!--Device-InputMethodProperty-readonly name: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## methodId

```TypeScript
readonly methodId: string
```

Unique identifier of the input method. Mandatory. <br> <br>Note: This API is supported since API version 8 and deprecated since API version 9. Use **id** instead.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [id](#id)

<!--Device-InputMethodProperty-readonly methodId: string--><!--Device-InputMethodProperty-readonly methodId: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## packageName

```TypeScript
readonly packageName: string
```

Input method package name. Mandatory. <br> <br>Note: This API is supported since API version 8 and deprecated since API version 9. Use **name** instead.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [name](#name)

<!--Device-InputMethodProperty-readonly packageName: string--><!--Device-InputMethodProperty-readonly packageName: string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
