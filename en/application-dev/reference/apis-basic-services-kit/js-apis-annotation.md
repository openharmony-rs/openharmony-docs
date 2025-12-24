# @ohos.annotation (Annotation)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Base-->
<!--Owner: @majiajun518-->
<!--Designer: @majiajun518-->
<!--Tester: @jiyong_sd-->
<!--Adviser: @fang-jinxu-->

This module defines the annotation types of OpenHarmony ArkTS APIs, such as the minimum available version of the lifecycle.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```
import { Available } from '@kit.BasicServicesKit';
```

## Available

@interface Available {
  minApiVersion: string = ''
}

Annotates the minimum available version supported by an API. This annotation capability is provided by the system and can be used on APIs such as classes, interfaces, variables, types, modules, and enums. After the annotation is added to the source code, the compilation tool checks for potential compatibility issues. If the value of **minApiVersion** is greater than that of **compatibleSDKVersion** specified in **build-profile.json5**, a compatibility warning is reported.

**Widget capability**: This API can be used in ArkTS widgets since API version 22.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Base

| Name| Type| Read-Only| Optional| Description                      |
| ---- | ---- | ---- | --- | -------------------------- |
| minApiVersion | string | No| No| Minimum available version, which consists of two parts: system type and version number. The system type can be omitted only when it is OpenHarmony, for example, **'OpenHarmony 20'** or **'20'**.|

**Example**

  ```ts
  import { Available } from '@kit.BasicServicesKit';

  @Available({minApiVersion: 'OpenHarmony 22'})
  function myFunc() {}

  @Available({minApiVersion: '22'}) //OpenHarmony default
  class MyClass {}
  ```
