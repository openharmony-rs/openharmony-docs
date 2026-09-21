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

**Examples**

```TypeScript
import { Available, deviceInfo } from '@kit.BasicServicesKit';

@Available({minApiVersion: 'OpenHarmony 22'}) // Annotate the minimum available version of the function.
function myFunc() {}

@Available({minApiVersion: '22'}) // Annotate the minimum available version of the class. The default system type is OpenHarmony.
class MyClass {}

// Not recommended: If the compatibleSdkVersion value set in the build-profile.json5 file in the project root directory is less than 22 and the myFunc method is directly called without version check, the compiler throws a warning at the call of myFunc, indicating that the method may fail to run on devices of earlier versions.
myFunc();

// Recommended approach 1: Use deviceInfo.sdkApiVersion to obtain the API version of system software for judgment, which can prevent exceptions on devices of earlier versions and eliminate compilation warnings.
if (deviceInfo.sdkApiVersion >= 22) {
  myFunc();
} else {
  // Select an approach for devices of earlier versions based on the service logic.
}

// Recommended approach 2: Annotate the start version information of @Available on the parent function (or class) where myFunc is called. If the new version number is not lower than the minimum available version of myFunc, the compilation warning is cleared.
@Available({minApiVersion: 'OpenHarmony 22'})
function myNewFunc() {
  myFunc();
}
```
