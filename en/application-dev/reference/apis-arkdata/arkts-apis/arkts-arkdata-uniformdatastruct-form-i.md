# Form

```TypeScript
interface Form
```

Represents the system-defined card typed data, which is used to share card information across applications. Typical usage scenarios include card drag-and-drop sharing, cross-application transfer of card content, and data sharing of home screen widgets.

**Since:** 15

<!--Device-uniformDataStruct-interface Form--><!--Device-uniformDataStruct-interface Form-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name corresponding to the card. It is recommended that the name follow the Ability component naming convention: a string no longer than 127 bytes, starting with a letter and containing letters, digits, underscores (_), or periods (.). Ensure that the name is unique within the entire application. The "package name.Ability name" format is recommended (for example, "com.example.myapplication.MainAbility").

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-abilityName: string--><!--Device-Form-abilityName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the card. The format must comply with the application package name specification.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-bundleName: string--><!--Device-Form-bundleName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | string | Uint8Array>
```

Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.

**Type:** Record&lt;string, number &#124; string &#124; Uint8Array&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-Form-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formId

```TypeScript
formId: number
```

Widget ID.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-formId: int--><!--Device-Form-formId: int-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formName

```TypeScript
formName: string
```

Widget name.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-formName: string--><!--Device-Form-formName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## module

```TypeScript
module: string
```

Module to which the widget belongs.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-module: string--><!--Device-Form-module: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.form'
```

Uniform data type, which has a fixed value of **openharmony.form**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'openharmony.form'

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

<!--Device-Form-readonly uniformDataType: 'openharmony.form'--><!--Device-Form-readonly uniformDataType: 'openharmony.form'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
