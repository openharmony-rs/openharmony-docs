# OpenHarmonyAppItem

Represents data of the home screen icon type defined by the system.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

Application ability name corresponding to the icon.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appIconId

```TypeScript
appIconId: string
```

Image ID of the icon.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appId

```TypeScript
appId: string
```

ID of the application, for which the icon is used.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appLabelId

```TypeScript
appLabelId: string
```

Label ID corresponding to the icon name.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
appName: string
```

Name of the application, for which the icon is used.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name corresponding to the icon.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

Object of the dictionary type used to describe the icon. The key is of the string type, and the value can be a number, a string, or a Uint8Array. By default, it is an empty dictionary object.

**Type:** Record&lt;string, number &#124; number &#124; number &#124; string &#124; Uint8Array&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.app-item'
```

Uniform data type, which has a fixed value of **openharmony.app-item**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'openharmony.app-item'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
