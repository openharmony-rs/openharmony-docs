# OpenHarmonyAppItem

```TypeScript
interface OpenHarmonyAppItem
```

Represents the system-defined desktop icon typed data, which is used to share desktop icon information across applications. Typical usage scenarios include dragging icons on the home screen launcher, sharing application icons in the app store, or creating shortcuts.

**Since:** 12

<!--Device-uniformDataStruct-interface OpenHarmonyAppItem--><!--Device-uniformDataStruct-interface OpenHarmonyAppItem-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name of the application corresponding to the icon. It is recommended that the name follow the Ability component naming convention: a string no longer than 127 bytes that starts with a letter and can contain letters, digits, underscores (_), or periods (.). Ensure that the name is unique within the entire application. The"package name.Ability name" format is recommended (for example, **"com.example.myapplication.MainAbility"**).

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-abilityName: string--><!--Device-OpenHarmonyAppItem-abilityName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appIconId

```TypeScript
appIconId: string
```

Image ID of the icon.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-appIconId: string--><!--Device-OpenHarmonyAppItem-appIconId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appId

```TypeScript
appId: string
```

ID of the application, for which the icon is used.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-appId: string--><!--Device-OpenHarmonyAppItem-appId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appLabelId

```TypeScript
appLabelId: string
```

Label ID corresponding to the icon name.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-appLabelId: string--><!--Device-OpenHarmonyAppItem-appLabelId: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
appName: string
```

Name of the application, for which the icon is used.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-appName: string--><!--Device-OpenHarmonyAppItem-appName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application corresponding to the icon. The format must comply with the application package name specification.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-bundleName: string--><!--Device-OpenHarmonyAppItem-bundleName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, number | string | Uint8Array>
```

Dictionary type object. The key is of the string type, and the value can contain data of the number (numeric type), string (string type), or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.

**Type:** Record&lt;string, number &#124; string &#124; Uint8Array&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-OpenHarmonyAppItem-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'openharmony.app-item'
```

Uniform data type, which has a fixed value of **openharmony.app-item**. For details, see [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md).

**Type:** 'openharmony.app-item'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OpenHarmonyAppItem-readonly uniformDataType: 'openharmony.app-item'--><!--Device-OpenHarmonyAppItem-readonly uniformDataType: 'openharmony.app-item'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
