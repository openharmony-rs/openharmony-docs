# ScannerOptionValue

```TypeScript
interface ScannerOptionValue
```

定义扫描仪选项值的接口。当对应选项的约束类型为SCAN_CONSTRAINT_STRING_LIST时，选项取值应为optionConstraintString集合中的字符串。

**起始版本：** 20

<!--Device-scan-interface ScannerOptionValue--><!--Device-scan-interface ScannerOptionValue-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## boolValue

```TypeScript
boolValue?: boolean
```

布尔值，仅在valueType为SCAN_TYPE_BOOL时有效。

**类型：** boolean

**起始版本：** 20

<!--Device-ScannerOptionValue-boolValue?: boolean--><!--Device-ScannerOptionValue-boolValue?: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## numValue

```TypeScript
numValue?: number
```

数值，仅在valueType为SCAN_TYPE_INT或SCAN_TYPE_FIXED时有效。

**类型：** number

**起始版本：** 20

<!--Device-ScannerOptionValue-numValue?: int--><!--Device-ScannerOptionValue-numValue?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## strValue

```TypeScript
strValue?: string
```

字符串值，仅在valueType为SCAN_TYPE_STRING时有效。

**类型：** string

**起始版本：** 20

<!--Device-ScannerOptionValue-strValue?: string--><!--Device-ScannerOptionValue-strValue?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## valueType

```TypeScript
valueType: OptionValueType
```

值类型，决定应使用的值字段。

**类型：** [OptionValueType](arkts-basicservices-scan-optionvaluetype-e.md)

**起始版本：** 20

<!--Device-ScannerOptionValue-valueType: OptionValueType--><!--Device-ScannerOptionValue-valueType: OptionValueType-End-->

**系统能力：** SystemCapability.Print.PrintFramework
