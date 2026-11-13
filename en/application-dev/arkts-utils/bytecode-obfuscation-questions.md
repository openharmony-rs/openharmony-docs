---
kits: ["ArkTS Kit / Ark Programming Language"]
description: "Summarizes common issues with ArkGuard bytecode obfuscation, including differences from source code obfuscation, troubleshooting approaches for functional exceptions, and handling methods for compilation errors and runtime exceptions, helping developers quickly locate and resolve obfuscation issues."
keywords: [obfuscation, bytecode obfuscation, common issues, obfuscation differences, functional exception troubleshooting, compilation errors, runtime exceptions]
doctype: faq
status: active
---

# Common Issues with ArkGuard in Bytecode Obfuscation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=c69025b6bd2fd85db9d4890282ea15305ba9aa08 translatedAt=2026-11-06T10:28:05.599Z pushedAt=2026-11-12T02:45:27.594Z nl=1 -->

## Differences Between Bytecode Obfuscation and Source Code Obfuscation

### Differences in Obfuscation Scope

**JSON Files**
When the `-enable-filename-obfuscation` option is enabled in bytecode obfuscation, JSON file names are obfuscated.

### Differences in Obfuscation Options

1. The bytecode obfuscation switch is disabled by default. After [enabling obfuscation](bytecode-obfuscation-guide.md#how-to-use), you need to configure `-enable-bytecode-obfuscation` in the `obfuscation-rules.txt` file in the module directory. If you need to retain debugging information, you also need to configure `-enable-bytecode-obfuscation-debugging`.
2. Bytecode obfuscation does not support the following obfuscation option `-remove-comments`.

### Differences in File Structure After Obfuscation

 **Directory Differences**

![bytecode-compilation-code-build](figures/bytecode-compilation-code-build.png) ![bytecode-compilation-build](figures/bytecode-compilation-build.png)

After bytecode obfuscation, the **obf** and **origin** folders and the **config.json** file are added to the **obfuscation** directory. For details, see [Viewing Obfuscation Effects](bytecode-obfuscation-guide.md#viewing-obfuscation-effects).

**File Content Differences**

nameCache.json file:

After source code obfuscation:

```json
{
  "entry/src/main/ets/entryability/EntryAbility.ets": {
    "IdentifierCache": {
      "#UIAbility": "UIAbility",
      "#testObject": "i",
      "#EntryAbility": "j"
    },
    "MemberMethodCache": {
      "onCreate:6:8": "onCreate",
      "onDestroy:10:12": "onDestroy",
      "onWindowStageCreate:14:25": "onWindowStageCreate",
      "onWindowStageDestroy:27:30": "onWindowStageDestroy",
      "onForeground:32:35": "onForeground",
      "onBackground:37:40": "onBackground"
    },
    "obfName": "entry/src/main/ets/entryability/EntryAbility.ets"
  },
  "compileSdkVersion": "5.0.0.70",
  "entryPackageInfo": "entry|1.0.0",
  "PropertyCache": {},
  "FileNameCache": {
    "Hide": "b"
  }
}
```

After bytecode obfuscation:

```json
{
  "entry/src/main/ets/entryability/EntryAbility.ets": {
    "IdentifierCache": {
      "#EntryAbility": "a",
      "#testObject": "c"
    },
    "MemberMethodCache": {
      "EntryAbility:0:0": "a",
      "onBackground:33:35": "onBackground",
      "onCreate:7:9": "onCreate",
      "onDestroy:10:12": "onDestroy",
      "onForeground:29:31": "onForeground",
      "onWindowStageCreate:14:23": "onWindowStageCreate",
      "onWindowStageDestroy:25:27": "onWindowStageDestroy"
    },
    "obfName": "entry/src/main/ets/entryability/EntryAbility.ets",
    "OriSourceFile": "entry|entry|1.0.0|src/main/ets/entryability/EntryAbility.ts",
    "ObfSourceFile": "entry|entry|1.0.0|src/main/ets/entryability/EntryAbility.ts"
  },
  "entryPackageInfo": "entry|1.0.0",
  "compileSdkVersion": "5.0.0.70",
  "PropertyCache": {},
  "FileNameCache": {
    "Hide": "b"
  }
}
```

1. Difference in bytecode obfuscation in **IdentifierCache**:
    1. Function parameter names are not obfuscated.
    2. There are no obfuscation name mappings for anonymous functions.
2. When the `-enable-filename-obfuscation` option is enabled, the `OriSourceFile` (source file path before obfuscation) and `ObfSourceFile` (source file path after obfuscation) fields are generated for bytecode obfuscation, but not for source code obfuscation.

### Precautions for Switching

**UI Component Obfuscation Differences**

Bytecode obfuscation does not provide UI component obfuscation capability.

Because UI components in bytecode contain a large number of string-form bound properties, methods, classes, variables, and so on, bytecode obfuscation has adopted a system trustlist scanning mechanism to ensure normal functionality.

**Binding Properties with Strings as Function Parameters**

Source code:

<!-- @[export_mainPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
@Component
export struct MainPage {
  @State messageStr: string = 'Hello World';

  build() {
  }
}
```

Intermediate file:

```abc
this.__messageStr = new ObservedPropertySimplePU('Hello World', this, "messageStr");
```

During the intermediate file conversion process, messageStr is bound in literal form; in this case, the messageStr property is obfuscated, but the string parameter of this method is not obfuscated, causing the UI to fail.

**Solution**: Collect all members in the struct and add them to the trustlist to exclude them from obfuscation. Currently, because bytecode obfuscation does not provide UI component obfuscation capability, the system automatically identifies and adds them to the trustlist, so no developer configuration is required.

**Binding Properties in Bytecode with Strings**

Source code:

<!-- @[import_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/Sample.ets) -->   

``` TypeScript
// Sample.ets
import { Type } from '@kit.ArkUI';

// Data center
@ObservedV2
class SampleChild {
  @Trace public p123: number = 0;
  public p2: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, @Type is required to ensure successful serialization
  @Type(SampleChild)
  @Trace public f123: SampleChild = new SampleChild();
}

@ObservedV2
class Info {
  @Trace public sample: Sample = new Sample();
}
```

Bytecode file:

```abc
tryldglobalbyname 0x136, Trace
sta v2
lda v0
ldobjbyname 0x137, prototype
sta v3
lda.str sample
sta v4
lda v2
callargs2 0x2c, v3, v4
lda v0
ldobjbyname 0x139, prototype
sta v2
lda.str sample
sta v3
lda v1
callargs2 0x2e, v2, v3
```

The bytecode contains a global **Trace** object that links properties using the string **sample**.

**Solution**: During bytecode obfuscation, the system scans for decorators and automatically add any parameters decorated with @Trace to the trustlist. Therefore, you do not need to set this up manually.

## Troubleshooting Functional Issues

**Procedure**

1. Configure the **-disable-obfuscation** option in the **obfuscation-rules.txt** file to disable obfuscation, and check whether the issue is caused by obfuscation.
2. If the issue is related to obfuscation, review the documentation to understand the capabilities of [obfuscation rules](bytecode-obfuscation.md#obfuscation-options) and understand when to [configure trustlists](bytecode-obfuscation.md#summary-of-existing-retention-options) to avoid issues.
3. If your issue matches any cases listed below, apply the suggested solutions.
4. If the issue is not covered, use a positive approach to identify the problem (remove specific configuration items if the corresponding functionality is not needed).
5. Analyze runtime crashes as follows:

    a. Open the application runtime log or click the Crash dialog that appears in DevEco Studio to find the runtime crash stack.

    b. The line numbers in the application runtime crash stack are the line numbers of the compiled artifact, and the method names may also be obfuscated names; therefore, when troubleshooting, it is recommended to directly inspect the compiled artifact based on the crash stack, then analyze which names cannot be obfuscated, and add them to the trustlist.

6. Analyze functional exceptions (for example, white screens) as follows:

    a. Open the application runtime log: select HiLog, search for logs directly related to the functional exception, and locate the context where the problem occurs.

    b. Locate the abnormal code segment: by analyzing the logs, find the specific code block that causes the functional exception.

    c. Enhance log output: in the suspected abnormal functional code, add log records for the processed data fields.

    d. Analyze and identify key fields: by analyzing the newly added log output, identify whether the field data is abnormal due to obfuscation.

    e. Configure the trustlist to protect key fields: add the key fields that are confirmed to directly affect application functionality after obfuscation to the trustlist.

## Handling Common Configuration Issues

### How to Handle the Failure to Generate a pa File When -enable-bytecode-obfuscation-debugging Is Enabled

First, ensure that Build Mode is set to release. Check build-profile.json5 in the root directory and set "compatibleSdkVersionStage": "beta3". Then check the obfuscation-rules.txt file in each module and enable the bytecode obfuscation option.

### Viewing Obfuscation Effects

After obfuscation is complete, intermediate products are generated. You can find the obfuscated intermediate products in the **build** directory of the compilation output, as well as the name mapping file and system API trustlist files.
-  Obfuscated file directory: build/default/[...]/release/obfuscation/obf
-  Directory of the name mapping file and system API trustlist file: build/default/[...]/release/obfuscation

![bytecode-build-product](figures/bytecode-build-product.png)

- Name mapping table file: nameCache.json. This file records the mapping relationships of bytecode name obfuscation.
- The system API trustlist file, named **systemApiCache.json**, records the APIs and property names that will be kept.


## Handling Compilation Errors

**Case 1: The error message "ERROR: [Class]get different name for method." is displayed.**

**Problem symptom**: When @CustomDialog is used to create a custom dialog box and another dialog box is popped up inside it, the build fails after bytecode obfuscation is enabled. The error message is:
Error message: ArkTSCompilerError: ArkTS:ERROR Failed to execute ByteCode Obfuscate.

Error message: [Class]get different name for method:&entry/src/main/ets/pages/XXXX&.#~@0>#setController^1.

<!-- @[export_build](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/SampleTmsDialog.ets) -->  

``` TypeScript
// Code 1
@CustomDialog
export default struct TmsDialog {
  controller?: CustomDialogController
  dialogController:CustomDialogController

  build() {
  }
}

// Code 2
@CustomDialog
struct Index{
  controller?: CustomDialogController
  dialogController?:CustomDialogController

  build() {
  }
}
```

**Possible Causes**

In this example, when a custom dialog box pops up another dialog box, or when two **CustomDialogController** objects are defined in a UI, the ETS code is converted to TS, resulting in two identical **setController** functions, causing the bytecode obfuscation to fail.

**Solution**

<!-- @[fix_build](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/SampleTmsDialog.ets) -->

``` TypeScript
@CustomDialog
export default struct TmsDialog {
  controller?: CustomDialogController
  dialogController:CustomDialogController|null = null;  // Modify the definition declaration here.

  build() {
  }
}
```

In code 1, the dialogController cannot be properly displayed up at runtime. You only need to change the code to the code in the solution. The dialogController will be displayed normally, and the bytecode obfuscation feature will work as expected.

In code 2, since only CustomDialogController is used, the @CustomDialog is not needed and can be directly removed. After removal, the function works normally, and the bytecode obfuscation feature works as expected.

From API version 18 onwards, the preceding sample code cannot be compiled properly. In the new version, one @CustomDialog component can have only one uninitialized CustomDialogController.

## Handling Runtime Exceptions

### Errors That May Occur When -enable-property-obfuscation Is Configured

**Case 1: The error message "Cannot read property 'xxx' of undefined" is reported.**

<!-- @[import_json](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ImportJson.ets) -->  

``` TypeScript
// Example JSON file structure (ImportJson.json):
/*
{
  "jsonObj": {
    "jsonProperty": "value"
  }
}
 */

// Before obfuscation:
import jsonData from './ImportJson.json';

let jsonProp = jsonData.jsonObj.jsonProperty;
```

``` TypeScript
// after obfuscation
import jsonData from "./ImportJson.json";

let jsonProp = jsonData.i.j;
```

After property name obfuscation is enabled, **jsonProperty** is obfuscated as a random character **j**. However, the original name is used in the JSON file, causing the error.
**Solution**: Use the **-keep-property-name** option to add the fields used in JSON files to the trustlist.

**Case 2: An error message is reported when database-related fields are used and property obfuscation is enabled.**

The error message is "table Account has no column named a23 in 'INSERT INTO Account(a23)'".

Database fields are used in the code. During obfuscation, the field names in the SQL statement are obfuscated, but the fields in the database retain their original names, which causes the error.
**Solution**: Use the -keep-property-name option to add the database fields in use to the trustlist.

**Case 3: Properties are obfuscated when Record<string, Object> is used as an object type.**

**Symptom**
When **Record<string, Object>** is used as an object type, properties like **linkSource** are obfuscated, causing the error. Example:

<!-- @[import_want](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/MainPage.ets) --> 

``` TypeScript
// Before obfuscation
import { Want } from '@kit.AbilityKit';
  // ...
  let petalMapWant: Want = {
    bundleName: 'com.example.myapplication',
    uri: 'maps://',
    parameters: {
      linkSource: 'com.other.app'
    }
  }
```

``` TypeScript
// After obfuscation:
import type Want from "@ohos:app.ability.Want";

let petalMapWant: Want = {
    bundleName: 'com.example.myapplication',
    uri: 'maps://',
    parameters: {
        i: 'com.other.app'
    }
};
```

**Possible Causes**

In this example, the object's properties need to be passed to the system to load a specific page, so the property names should not be obfuscated. The type **Record<string, Object>** is a generic definition for an object with string keys and does not describe the internal structure or property types in detail. Therefore, the obfuscation tool cannot identify which properties should not be obfuscated, leading to the obfuscation of internal property names like **linkSource**.

**Solution**

Add the problematic property names to the property trustlist. The following is an example:

```txt
-keep-property-name
linkSource
```

**Case 4: Properties of decorators marked with @Type and @Trace do not work properly after obfuscation.**

**Symptom**

The properties of decorators marked with @Type and @Trace can be obfuscated properly, but the functionality becomes abnormal.

<!-- @[export_decorator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/SampleChild.ets) -->     

``` TypeScript
// SampleChild.ets
import { Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace public p123: number = 0;
  public p2: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use @Type to modify them to ensure successful serialization.
  @Type(SampleChild)
  @Trace public f123: SampleChild = new SampleChild();
}
```

<!-- @[call_decorator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/CallDecorator.ets) -->

``` TypeScript
// Call the API
// CallDecorator.ets
import { PersistenceV2 } from '@kit.ArkUI';
import { Sample } from './SampleChild';

@Entry
@ComponentV2
export struct Page {
  prop: Sample = PersistenceV2.connect(Sample, () => new Sample())!;

  build() {
    Column() {
      Text(`Page1 add 1 to prop.f123.p123: ${this.prop.f123.p123}`)
    }
  }
}
```

After obfuscation, **p123** and **f123** are correctly replaced, but when processing the **Trace** and **Type** decorator properties, **p123** and **f123** are identified as strings and not obfuscated, leading to failed calls.

**Possible Causes**

Decorator-marked property names should be retained, and properties decorated with the combination of @Type and @Trace decorators should also be retained.

**Solution**

Use the **-keep-property-name** option to add properties within types that are not directly exported to the trustlist. Example:

```txt
-keep-property-name
f123
p123
```

**Case 5: Problems that may occur when both -enable-property-obfuscation and -keep are enabled.**

**Symptom**
The following obfuscation configuration is used:

```txt
-enable-property-obfuscation
-keep
./ExportInterface.ts
```

Also import the interface of ExportInterface.ts in MainPage.ets. In this case, a property in the interface has an object type. The properties of this object type are kept in ExportInterface.ts but obfuscated in MainPage.ets, which causes a functional exception when the property is called. Example:

<!-- @[export_myInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportInterface.ts) -->

``` TypeScript
// Before obfuscation
// ExportInterface.ts
export interface MyInfo {
  age: number;
  address: {
    city1: string;
  }
}
```

<!-- @[import_myInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/MainPage.ets) -->   

``` TypeScript
// MainPage.ets
import { MyInfo } from './ExportInterface';
  // ...
  const person: MyInfo = {
    age: 20,
    address: {
      city1: 'shanghai'
    }
  }
```

``` TypeScript
// After obfuscation, the code in ExportInterface.ts is retained
// MainPage.ets
import { MyInfo } from './ExportInterface';

const person: MyInfo = {
    age: 20,
    address: {
        i: "shanghai"
    }
}
```

**Possible Causes**

When the -keep option keeps the ExportInterface.ts file, the code in ExportInterface.ts is not obfuscated. For the properties within the type to which an exported property (such as address) belongs, they are not automatically collected into the property trustlist. Therefore, when the properties within this type are used in other files, they are obfuscated.

**Solution**

Solution 1: Define the property type using **interface** and export it. This will automatically add the property to the trustlist. Example:

<!-- @[export_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportCompositeInterface.ts) -->

``` TypeScript
// ExportCompositeInterface.ts
export interface AddressType {
  city1: string
}
export interface MyInfo {
  age: number;
  address: AddressType;
}
```

Solution 2: Use the **-keep-property-name** option to add properties within types that are not directly exported to the trustlist. Example:

``` TypeScript
-keep-property-name
city1
```

### Errors That May Occur When -enable-export-obfuscation and -enable-toplevel-obfuscation Are Configured

When the two options are configured, method name confusion in the following scenarios is involved when the main module calls the methods of other modules:
|Main Module|Dependent Module|Imported/Exported Name Obfuscation|
|-------|--------|---------|
|HAP/HSP|HSP|The HSP and main module are built independently, and different names are generated after obfuscation. Therefore, a trustlist must be configured for both the HSP and main module.|
|HAP/HSP|Local HAR|The local HAR is built together with the main module. After obfuscation, the names are the same.|
|HAP/HSP|Third-party library|The names and properties exported from a third-party library are collected to the trustlist. They are not confused during import and export.|

For the HSP, you must add the methods used by other modules to the trustlist. You must add the same trustlist for the main module. Therefore, you are advised to add the obfuscation file configured with the trustlist (for example, **hsp-white-list.txt**) to the obfuscation configuration item of the module that depends on the obfuscation file, that is, the **files** field shown in the following figure.

![bytecode-buildoptionset](figures/bytecode-buildoptionset.png)

**Case 1: When a class is dynamically imported, the class definition is confused, but the class name is not, causing an error.**
<!-- @[export_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportUtils.ts) -->

``` TypeScript
// before obfuscation
// ExportUtils.ts
export function add(a: number, b: number): number {
  return a + b;
}
```

<!-- @[import_utils](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/MainPage.ets) --> 

``` TypeScript
// MainPage.ets
async function loadAndUseAdd() {
    try {
        const mathUtils = await import('./ExportUtils');
        const result = mathUtils.add(2, 3);
    } catch (error) {
        console.error('Failure reason:', error);
    }
}

loadAndUseAdd();
```

``` TypeScript
// after obfuscation
// ExportUtils.ts
export function c1(d1: number, e1: number): number {
    return d1 + e1;
}
```

``` TypeScript
// After obfuscation:
// MainPage.ets
async function i() {
    try {
        const a1 = await import("@normalized:N&&&entry/src/main/ets/pages/ExportUtils&");
        const b1 = a1.add(2, 3);
    }
    catch (z) {
        console.error('Failure reason:', z);
    }
}
i();
```

The **add** function is in the top-level scope when it is defined, but is considered as a property when it is accessed through **.add**. Because the **-enable-property-obfuscation** option is not configured, the property name is not obfuscated during the call.

**Solution**

Solution 1: Configure the **-enable-property-obfuscation** option.

Solution 2: Use **-keep-global-name** to configure **add** to the trustlist.


**Case 2: For a method in a namespace, the method definition is confused, but the statement that uses the method is not, causing an error.**

<!-- @[export_ns](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportNs.ts) -->

``` TypeScript
// Before obfuscation
// ExportNs.ts
export namespace NS {
  export function foo() {
    console.info(`export NS function foo is called`);
  }
}
```

<!-- @[import_ns](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/MainPage.ets) --> 

``` TypeScript
// MainPage.ets
import { NS } from './ExportNs';
  // ...
  NS.foo();
```

``` TypeScript
// After obfuscation:
// ExportNs.ts
export namespace i {
    export function j() {}
}
```

``` TypeScript
// after obfuscation
// MainPage.ets
import { i } from './ExportNs';

i.foo();
```

**foo** in the namespace is an export element and is considered as a property when being called by **NS.foo**. Because the **-enable-property-obfuscation** option is not configured, the property name is not obfuscated during the call.

**Solution**

1. Configure the **-enable-property-obfuscation** option.
2. Use the **-keep-global-name** option to add the methods exported from the namespace to the trustlist.

**Case 3: When declare global is used, a syntax error is reported after obfuscation.**

<!-- @[declare_global](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportInterface.ts) -->

``` TypeScript
// ExportInterface.ts
// Before obfuscation.
declare global {
  var myAge : string
}
```

``` TypeScript
// After obfuscation:
declare a2 {
    var b2 : string
}
```

The error message "SyntaxError: Unexpected token" is reported.

**Solution**

Use **-keep-global-name** to add **global** to the trustlist.

Since API version 18, **global** has been added to the system trustlist. You do not need to configure **-keep-global-name**.

**Case 4: When Reflect.defineMetadata() is used, a message is displayed indicating that the function cannot be found after obfuscation.**

**Symptom**

After the -enable-toplevel-obfuscation option (top-level scope name obfuscation) is enabled, obfuscation succeeds during bytecode obfuscation, but a runtime exception is reported. The error log is as follows:

```txt
Error message: is not callable
Stacktrace: Cannot get SourceMap info, dump raw stack: at anonymous (ads_service|@hw-ads/ohos-ads-model|1.0.1|src/main/ets/annotations/FieldType.ts:6:1.
```

``` JSON5
// oh-package.json5
"dependencies": {
  "reflect-metadata": "0.2.1"
}
```

``` TypeScript
// test.ts
import 'reflect-metadata';

// Call the code.
export const FIELD_TYPE_KEY = Symbol('fieldType');
export function FieldType(...types: Function[]): PropertyDecorator {
    return (target, key) => {
        Reflect.defineMetadata(FIELD_TYPE_KEY, types, target, key);
    };
}
```

**Possible cause**

After the -enable-toplevel-obfuscation option (top-level scope name obfuscation) is enabled, in the Reflect file, function names participate in obfuscation, while the string "defineMetadata" in the exporter function is excluded from obfuscation. As a result, when Reflect.defineMetadata is used externally, the corresponding function cannot be found.

**Solution**

Use **-keep-global-name** to add **defineMetadata** to the trustlist. Since the Reflect file uses exporter multiple times, you are advised to use the **-keep** option directly.

```txt
-keep
../xxx/xxx/xxx/Reflect.ts  // Use the relative path of the file.
```

### The **-enable-string-property-obfuscation** option is not configured, but the string literal property name is obfuscated. As a result, the value of the string literal property name is undefined.

<!-- @[fix_age](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForBytecodeObfuscation/BytecodeObfuscationIssues/entry/src/main/ets/pages/ExportInterface.ts) -->

``` TypeScript
// ExportInterface.ts
// Before obfuscation
const person = {
  myAge: 18
}
person["myAge"] = 20;
```

``` TypeScript
// file.ts
// After obfuscation:
const person = {
    myAge: 18
}
person["m"] = 20;
```

**Solution**

1. Check whether **-enable-string-property-obfuscation** is configured for the dependent HAR. If it is configured, the main project will be affected, and you should disable it.
2. If it must be configured, add the property name to the trustlist.
3. If it is not configured and the SDK version is earlier than 4.1.5.3, update the SDK.

### Errors That May Occur When -enable-filename-obfuscation Is Configured

**Case 1: The error message "Error Failed to get a resolved OhmUrl for 'D:code/MyApplication/f12/library1/pages/d.ets' imported by 'undefined'" is reported.**

As shown below, the outer layer of the **library1** module contains a directory named **directory**. When file name obfuscation is enabled, **directory** is obfuscated as **f12**, causing the error indicating that the path is not found.

![bytecode-directory](figures/bytecode-directory.png)

**Solution**

1. If the project directory structure and error message are similar, update the SDK to 5.0.0.26 or later.
2. Use the **-keep-file-name** option to add the directory name **directory** of the module to the trustlist.

**Case 2: The error message "Cannot find module 'ets/appability/AppAbility' which is application Entry Point" is reported.**

The system loads the ability file when the application is running. Therefore, you must manually configure the trustlist to prevent the specified file from being obfuscated.
**Solution**: Use the **-keep-file-name** option to add the path corresponding to the **srcEntry** field in the **src/main/module.json5** file to the trustlist.

```txt
-keep-file-name
appability
AppAbility
```

The HAP and HSP depend on the same local source code HAR module.

* If file name obfuscation is enabled, the following issue may occur:
    Singleton function exceptions: The reason is that the HAP and HSP modules execute independent build and obfuscation processes. The same file names in the shared local source code HAR may be obfuscated differently in the HAP and HSP packages.
    Interface call failures: The reason is that the HAP and HSP modules execute independent build and obfuscation processes. Different file names in the shared local source code HAR may be obfuscated to the same name in the HAP and HSP packages.
* If **-enable-export-obfuscation** and **-enable-toplevel-obfuscation** are configured, the interface loading failures may occur at runtime.

    The HAP and HSP modules execute independent build and obfuscation processes, resulting in different obfuscated names for the interfaces exposed by the shared local source code HAR.

**Solution**

1. Convert the local source code HAR that both the HAP and HSP depend on into a bytecode HAR. In this way, this HAR will not be obfuscated again when it is depended on.
2. Build and package the local source code HAR that is depended on by both the HAP and HSP in release mode. In this way, when this HAR is depended on, its filenames and exposed interfaces will not be obfuscated.
