# Configuring arkOptions in build-profile.json5
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @huyunhui1; @liyancheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=9a6cf8426179729a05b00282d51b2f4f5b82becb translatedAt=2026-10-13T07:34:58.455Z pushedAt=2026-10-15T08:47:06.478Z -->

## Overview

arkOptions mainly provides ArkTS compilation-related configurations. This document describes the types configuration type and the maxFlowDepth configuration for the maximum control flow analysis depth in arkOptions. For other configuration items in arkOptions, see [build-profile.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-configuration-file-overview).

## types

### Description

  Field **types** in **arkOptions**

| Name| Description| Configuration Scope| Data Type| Optional|
| -------- | -------- | -------- | -------- | -------- |
| types | Specifies type declaration files to be globally imported, avoiding the need to import them individually in each source file.| Module-level| Array| Optional, defaults to an empty array|

### Example

Below provides an example configuration of the **types** Field in **arkOptions**.

Add the **types** field to the **arkOptions** property in the **buildOption** section of the module-level **build-profile.json5** file.

<!-- @[add_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkoptionsGuide/entry/build-profile.json5) --> 

``` JSON5
// In /entry/build-profile.json5
"arkOptions": {
  "types": ["pako", "./oh_modules/@types/mime", "./src/main/ets/pages/global"]
}
```

The types field supports specifying a package name, a relative path to a package, or a relative path to a declaration file. The type search scope is limited to the current module. If files with the same name (different extensions) exist in a directory, the default loading order is .d.ets > .d.ts, that is, files with the .d.ets extension are loaded first.
1. Package name method: search for the declaration file defined by the package name in the oh_modules/@types/ directory, for example, "pako".<br />
2. Relative path to a package method: supports searching for the declaration file defined in a relative path based on build-profile.json5, for example, "./oh_modules/@types/mime".<br />
3. Relative path to a declaration file method: supports searching for the declaration file in a relative path, for example, "./src/main/ets/pages/global".

### Precautions

If you specify a package name or a relative path to a package in the types field, configure the dependencies field in the oh-package.json5 file under the entry module as follows:
<!-- @[dependencies](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkoptionsGuide/entry/oh-package.json5) -->

``` JSON5
"dependencies": {
  "@types/pako": "latest",
  "@types/mime": "latest"
}
```

If you specify a relative path to a declaration file in the **types** field, ensure the corresponding declaration file exists in the module. Below is the content of a declaration file named **global.d.ts** in **src/main/ets/pages**:
<!-- @[declare_global](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkoptionsGuide/entry/src/main/ets/pages/global.d.ts) --> 

``` TypeScript
declare namespace Global {
  type ObjectType = string | number;
}
```

After configuring types, you can use these global types in your code:
<!-- @[test_party](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkoptionsGuide/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
// In entry/src/main/ets/pages/Index.ets
let testPako: pako.constants = 0;
let testMime: mime.TypeMap = {};
let testGlobal: Global.ObjectType = 'test';
```

## maxFlowDepth

### Description

Configuration file tag description of the maxFlowDepth field in tscConfig under arkOptions:

| Name| Description| Configuration Scope| Data Type| Optional|
| -------- | -------- | -------- | -------- | -------- |
| maxFlowDepth | Developers use the maxFlowDepth field to customize the maximum depth of tsc control flow analysis during tsc compilation, avoiding compilation errors caused by a fixed maximum depth. The minimum configurable value of this configuration item is 2000, and the maximum configurable value is 65535. | Project-level | Numeric | This tag can be omitted. When omitted, the default maximum depth of tsc control flow analysis, 2000, is used. |

### Example

Display of the maxFlowDepth field in arkOptions/tscConfig.

Add the maxFlowDepth field to the arkOptions/tscConfig property in the buildOption tag of the build-profile.json5 configuration file in the project-level directory.

<!-- @[add_tscConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkoptionsGuide/build-profile.json5) --> 

``` JSON5
// In projectName/build-profile.json5
"arkOptions": {
  "tscConfig": {
    "maxFlowDepth": 2222
  }
}
```

### Precautions

- The **maxFlowDepth** field can only be configured in the project-level **build-profile.json5** file.
- If the value configured for the maxFlowDepth field exceeds the allowed range, compilation and build errors will occur.

  ```txt
   hvigor ERROR: Schema validate failed.
    Detail: Please check the following fields.
      {
         instancePath: 'app.products[0].buildOption.arkOptions.tscConfig.maxFlowDepth',
         keyword: 'maximum',
         params: { comparison: '<=', limit: 65535 },
         message: 'must be <= 65535',
         location: 'D:/projectName/build-profile.json5:rowNo:columnNo'
      }
  ```

- If a function or module in the code is too long, causing the control flow analysis depth to exceed the value configured for this field or the default value, the control flow analysis is terminated and an error is reported: The containing function or module body is too large for control flow analysis.

## transformLib

### Description

Field **transformLib** in **arkOptions**

| Name| Description| Configuration Scope| Data Type| Optional|
| -------- | -------- | -------- | -------- | -------- |
| transformLib | Specifies the bytecode instrumentation plugin configuration, allowing you to modify bytecode during compilation. This field is supported only in the stage model. The format is a relative path to the dynamic library that does the instrumentation. The dynamic library must be generated on the corresponding platform and cannot be copied or renamed across platforms.| Module-level| String| Optional, defaults to not using this feature|

### Example

Below provides an example configuration of the **transformLib** Field in **arkOptions**.

Add the **transformLib** field to the **arkOptions** property in the **buildOption** section of the module-level **build-profile.json5** file.
```json
{
  "buildOption": {
    "arkOptions": {
      "transformLib": "./dll/example.dll"
    }
  }
}
```
For details about how to modify Ark bytecode, see [Customizing Ark Bytecode During Compilation](customize-bytecode-during-compilation.md).

### Precautions

- If this field is not configured, the feature is not used by default.
- The configuration takes effect for HAP and HSP modules immediately. For HAR modules, only bytecode HAR configurations are effective; non-bytecode HAR configurations are ignored.
- The file format must be .dll (for Windows) or .so (for Linux/macOS).