# Form

Represents data of the widget type defined by the system.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name corresponding to the widget.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle to which the widget belongs.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

Object of the dictionary type used to describe the icon. The key is of the string type, and the value can be a number, a string, or a Uint8Array. By default, it is an empty dictionary object.

**Type:** Record&lt;string, number &#124; number &#124; number &#124; string &#124; Uint8Array&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formId

```TypeScript
formId: number
```

Widget ID.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formName

```TypeScript
formName: string
```

Widget name.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## module

```TypeScript
module: string
```

Module to which the widget belongs.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.form'
```

Uniform data type, which has a fixed value of **openharmony.form**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'openharmony.form'

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
