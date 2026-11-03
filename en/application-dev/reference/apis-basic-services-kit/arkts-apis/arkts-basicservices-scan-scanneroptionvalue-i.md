# ScannerOptionValue

```TypeScript
interface ScannerOptionValue
```

Defines the scanner option value. When the constraint type of the option is **SCAN_CONSTRAINT_STRING_LIST**, the option value must be a string in the **optionConstraintString** set.

**Since:** 20

<!--Device-scan-interface ScannerOptionValue--><!--Device-scan-interface ScannerOptionValue-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## boolValue

```TypeScript
boolValue?: boolean
```

Boolean. This parameter is valid only when **valueType** is set to **SCAN_TYPE_BOOL**.

**Type:** boolean

**Since:** 20

<!--Device-ScannerOptionValue-boolValue?: boolean--><!--Device-ScannerOptionValue-boolValue?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## numValue

```TypeScript
numValue?: number
```

Numeric value. This parameter is valid only when **valueType** is set to **SCAN_TYPE_INT** or **SCAN_TYPE_FIXED**.

**Type:** number

**Since:** 20

<!--Device-ScannerOptionValue-numValue?: int--><!--Device-ScannerOptionValue-numValue?: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## strValue

```TypeScript
strValue?: string
```

String value. This parameter is valid only when **valueType** is set to **SCAN_TYPE_STRING**.

**Type:** string

**Since:** 20

<!--Device-ScannerOptionValue-strValue?: string--><!--Device-ScannerOptionValue-strValue?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## valueType

```TypeScript
valueType: OptionValueType
```

Value type, which determines the value field to be used.

**Type:** [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md)

**Since:** 20

<!--Device-ScannerOptionValue-valueType: OptionValueType--><!--Device-ScannerOptionValue-valueType: OptionValueType-End-->

**System capability:** SystemCapability.Print.PrintFramework
