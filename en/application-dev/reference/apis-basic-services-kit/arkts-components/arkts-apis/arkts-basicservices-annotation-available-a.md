# Available

```TypeScript
export @interface Available
```

Annotates the minimum available version supported by an API. This annotation capability can be used on classes, interfaces, functions, variables, types, modules, and enums. After the annotation is added to the source code, the compilation tool checks for potential compatibility issues. If the value of minApiVersion is greater than that of compatibleSdkVersion specified in build-profile.json5, a compatibility warning is reported.

**Since:** 22

**System capability:** SystemCapability.Base

## Modules to Import

```TypeScript
import { Available, SuppressWarnings, SuppressWarningsType } from '@kit.BasicServicesKit';
```

## minApiVersion

```TypeScript
minApiVersion: string = ''
```

Minimum available version, which consists of two parts: system type and version number. The system type can be omitted only when it is OpenHarmony, for example, 'OpenHarmony 20' or '20'. If the value of **minApiVersion** is greater than that of compatibleSdkVersion specified in build-profile.json5, a compatibility warning is reported. If a value in an invalid format is passed, the compiler reports an error indicating that the format is incorrect.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Base
