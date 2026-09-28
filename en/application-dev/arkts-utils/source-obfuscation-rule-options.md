# ArkGuard Obfuscation Configuration Options

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=76413f655ee0ef537da838554c380a0edb4adb50 translatedAt=2026-08-31T12:44:08.201Z pushedAt=2026-08-31T15:26:46.600Z -->

Starting from API version 10, ArkGuard provides obfuscation configuration options to control the obfuscation effect. Developers can customize these options in the [obfuscation-rules.txt](./source-obfuscation-guide.md) file. If obfuscation is enabled but no options are configured, only the default obfuscation effect is applied, that is, obfuscating local variable and parameter names.

## Obfuscation Option Summary

| Function | Option | Initial API Version |
| --- | --- | --- |
| Disable obfuscation | [`-disable-obfuscation`](#-disable-obfuscation) | 10 |
| Enable property name obfuscation | [`-enable-property-obfuscation`](#-enable-property-obfuscation) | 10 |
| Enable string property name obfuscation | [`-enable-string-property-obfuscation`](#-enable-string-property-obfuscation) | 10 |
| Enable top-level scope name obfuscation | [`-enable-toplevel-obfuscation`](#-enable-toplevel-obfuscation) | 10 |
| Enable import/export name obfuscation | [`-enable-export-obfuscation`](#-enable-export-obfuscation) | 10 |
| Enable file name obfuscation | [`-enable-filename-obfuscation`](#-enable-filename-obfuscation) | 10 |
| Code compression | [`-compact`](#-compact) | 10 |
| Remove comments from declaration files | [`-remove-comments`](#-remove-comments) | 10 |
| Remove console.* statements | [`-remove-log`](#-remove-log) | 10 |
| Output name cache | [`-print-namecache`](#-print-namecache) | 10 |
| Reuse name cache | [`-apply-namecache`](#-apply-namecache) | 10 |
| Output unobfuscated name list | [`-print-kept-names`](#-print-kept-names) | 18 |
| Reduce language preset whitelist | [`-extra-options strip-language-default`](#-extra-options-strip-language-default) | 18 |
| Reduce system preset whitelist | [`-extra-options strip-system-api-args`](#-extra-options-strip-system-api-args) | 18 |
| Do not keep names of modules not involved in compilation | [`-extra-options strip-not-compiled-module-name`](#-extra-options-strip-not-compiled-module-name) | 22 |
| Keep declaration file parameters | [`-keep-parameter-names`](#-keep-parameter-names) | 18 |
| Merge dependency module options | [`-enable-lib-obfuscation-options`](#-enable-lib-obfuscation-options) | 18 |
| Mark whitelist in source code via comments | [`-use-keep-in-source`](#-use-keep-in-source) | 19 |
| Keep object literal property names | [`-keep-object-props`](#-keep-object-props) | 23 |
| Remove specified method call statements | [`-remove-nosideeffects-calls`](#-remove-nosideeffects-calls) | 23 |

## -disable-obfuscation

Disables all obfuscation.

After this option is configured, the default obfuscation (which only obfuscates local variable and parameter names) and all other configured obfuscation options and keep options become invalid.

## -enable-property-obfuscation

> **Note**:
>
> After this option is enabled, in scenarios that require manual whitelist configuration, configure the corresponding property names into the whitelist.

After this option is configured, property name obfuscation is enabled, with the following effect:

  <!-- @[optionExample_enablePropertyObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  class TestA {
    static prop1: number = 0;
  }
  TestA.prop1;
  ```

  ``` TypeScript
  // After obfuscation:
  class TestA {
    static i: number = 0;
  }
  TestA.i;
  ```

After this option is configured, all property names will be obfuscated, except in the following scenarios:

* When the `-enable-export-obfuscation` option is not enabled, property names of classes or objects directly imported or exported via `import/export` will not be obfuscated. For example, the property name `data1` in the following example will not be obfuscated.

  <!-- @[optionExample_enablePropertyObfuscation2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->  

  ``` TypeScript
  // ArkGuardAbility.ts
  export class MyClass01 {
    data1: string;
  }
  ```

* Property names in ArkUI components will not be obfuscated. For example, `message` and `data` in the following example will not be obfuscated.

  <!-- @[etsOptionExample_enablePropertyObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) --> 

  ``` TypeScript
  // ArkGuardAbility.ets
  @Component struct MyExample {
    @State message: string = "hello";
    data: number[] = [];
    // ...
    build() {
    }
  }
  ```

* Property names specified by the keep option -keep-property-name will not be obfuscated.

* Property names in the SDK API list will not be obfuscated. The SDK API list is a name list automatically extracted from the SDK at build time. Its cache file is systemApiCache.json, located at project directory/build/default/cache/{...}/release/obfuscation.

* String literal property names are not obfuscated, and property names identical to them are not obfuscated either. For example, `exampleName` and `exampleAge` in the following example are not obfuscated.

  <!-- @[optionExample_enableStringPropertyObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

  ``` TypeScript
  // Before obfuscation:
  // ArkGuardAbility.ts
  let person = {"exampleName": "abc"};
  person["exampleAge"] = 22;
  ```

  <!-- @[optionExample_enablePropertyObfuscation3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  let person1 = {exampleName: "aaa"};
  let name = person1.exampleName;
  ```

* Annotation member names are not obfuscated. For example, `authorName` and `revision` in the following example are not obfuscated.

  <!-- @[etsOptionExample_enablePropertyObfuscation2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) -->

  ``` TypeScript
  @interface MyAnnotation1 {
    authorName: string;
    revision: number = 1;
  }
  ```

## -enable-string-property-obfuscation

To obfuscate string literal property names, use this option with `-enable-property-obfuscation` enabled.

  ```text
  -enable-property-obfuscation
  -enable-string-property-obfuscation
  ```

Based on the configuration above, the obfuscation results of `exampleName` and `exampleAge` are as follows:

  <!-- @[optionExample_enableStringPropertyObfuscation1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  // ArkGuardAbility.ts
  let person = {"exampleName": "abc"};
  person["exampleAge"] = 22;
  ```

  ``` TypeScript
  // After obfuscation:
  // example.ts
  let person = {"a": "abc"};
  person["b"] = 22;
  ```

**Note the following when using this option:**

1. If the code contains string property names with special characters (characters other than `a-z, A-Z, 0-9, _`), for example, `let obj = {"\n": 123, "": 4, " ": 5}`, it is recommended not to enable the `-enable-string-property-obfuscation` option, because these names may not be preserved through -keep-property-name.

2. The property whitelist of the SDK API does not include the string constant values used in the declaration file. For example, the string 'ohos.want.action.home' in the example is not included in the property whitelist.

   <!-- @[optionExample_enableStringPropertyObfuscation2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) --> 

   ``` TypeScript
   // SDK API file @ohos.app.ability.wantConstant snippet:
   export enum Params {
     ACTION_HOME = 'ohos.want.action.home'
   }
   
   // Developer source code example:
   const obj1: Record<string, string> = {
     'ohos.want.action.home': 'value'
   }
   let params = obj1['ohos.want.action.home'];
   ```

Therefore, after enabling the `-enable-string-property-obfuscation` option, if you want to keep the properties of SDK API string constants used in the code from being obfuscated, such as obj['ohos.want.action.home'], you can use the -keep-property-name option to keep them.

## -enable-toplevel-obfuscation

> **Note**:
>
> After this option is enabled, in scenarios where manual Whitelist configuration is required, configure the corresponding top-level scope names into the Whitelist.

Enable top-level scope name obfuscation. The effect is as follows:

  <!-- @[optionExample_enableToplevelObfuscation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  let count = 0;
  ```

  ``` TypeScript
  // After obfuscation:
  let s = 0;
  ```

After this option is configured, all top-level scope names are obfuscated, except in the following scenarios:

* When the `-enable-export-obfuscation` option is not enabled, names directly imported or exported by `import/export` are not obfuscated.

* Names whose declarations cannot be found in the current file are not obfuscated.

* Top-level scope names specified by the keep option -keep-global-name are not obfuscated.

* Top-level scope names in the SDK API list are not obfuscated.

## -enable-export-obfuscation

Enables obfuscation of directly imported or exported names. The effect is as follows:

  <!-- @[optionExample_enableExportObfuscation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  namespace ns {
    export type customT = string;
  }
  ```

  ``` TypeScript
  // After obfuscation:
  namespace ns {
    export type h = string;
  }
  ```

If only this option is configured, only the names imported or exported in non-top-level scopes are obfuscated. **To obfuscate names imported or exported in the top-level scope, use this option together with `-enable-toplevel-obfuscation`; to obfuscate imported or exported property names, use this option together with `-enable-property-obfuscation`.** When this option is enabled, the following special scenarios are not obfuscated:

* Names and property names exported from remote HAR packages (whose real paths are in oh_modules) are not obfuscated.

* Names and property names specified by the ArkGuard obfuscation keep options are not obfuscated.

* Names in the SDK API list are not obfuscated.

## -enable-filename-obfuscation

> **Note**:
>
> After this option is enabled, in scenarios that require manual whitelist configuration, configure the corresponding folder/file names into the whitelist.

Enables file/folder name obfuscation. The effect is as follows:

  <!-- @[testOptionExample_enableFilenameObfuscation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/FilenameObfuscationTest/FilenameObfuscationTest.ts) -->        

  ``` TypeScript
  // FilenameObfuscationTest/FilenameObfuscationTest.ts
  export function foo () {}
  ```

  <!-- @[optionExample_enableFilenameObfuscation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

  ``` TypeScript
  // ArkGuardAbility.ts
  // Before obfuscation:
  import * as m from '../FilenameObfuscationTest/FilenameObfuscationTest';
  import { foo } from '../FilenameObfuscationTest/FilenameObfuscationTest';
  // ...
  m.foo();
  foo();
  async function func1() {
    const modules = await import('../FilenameObfuscationTest/FilenameObfuscationTest');
    const result = modules.foo();
  }
  ```

  ``` TypeScript
  // example.ts
  // After obfuscation:
  import * as m from "@normalized:N&&&entry/src/main/ets/c/d&";
  import { foo } from "@normalized:N&&&entry/src/main/ets/c/d&";
  m.foo();
  foo();
  async function func() {
      const f = await import("@normalized:N&&&entry/src/main/ets/c/d&");
      const g = f.foo();
  }
  ```

After this option is configured, all file and folder names will be obfuscated, except in the following scenarios:

* File/folder names configured in the 'main' and 'types' fields of the oh-package.json5 file will not be obfuscated.

* File/folder names configured in the 'srcEntry' field of the module.json5 file within the module will not be obfuscated.

* File/folder names specified by -keep-file-name will not be obfuscated.

* Non-ECMAScript module reference methods (for example: `const module = require('./module')`).

* Non-path reference methods, for example, `json5` in `import module from 'json5'` will not be obfuscated.

>**Note**:
>
>Because the system loads certain specified files when the application is running, for such files, developers need to manually configure the corresponding whitelist in the -keep-file-name option to prevent the specified files from being obfuscated, which would cause runtime failures.
>
>The three types of file names that cannot be obfuscated—compilation entry, Ability component, and Worker multithreading—have been automatically collected into the whitelist in DevEco Studio 5.0.3.500 and later versions, so no manual configuration is required. Other scenarios where file names cannot be obfuscated still require manual configuration by developers.

## -compact

Removes whitespace characters that do not participate in the syntax structure and do not affect program execution, as well as all line breaks.

After this option is configured, all code is compressed into a single line. The effect is as follows:

  <!-- @[optionExample_compact](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  class TestA {
    static prop1: number = 0;
  }
  TestA.prop1;
  ```

  ``` TypeScript
  // After obfuscation:
  class TestA { static prop1: number = 0; } TestA.prop1;
  ```

>**Note**:
>
>For an application built in release mode, the stack information contains only code line numbers, not column numbers. Therefore, after the -compact feature is enabled, the line number in the error stack cannot be used to precisely locate the specific statement in the source code.
>
>If you want to keep line breaks for some source code paths (to facilitate reading the obfuscated intermediate product against the error stack line numbers), you can use -keep-uncompact while enabling `-compact` to specify the source code paths that do not participate in compression.

## -remove-comments

Deletes JSDoc comments from the generated declaration files. The effect is as follows:

Before obfuscation:

  <!-- @[optionExample_removeComments](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  /**
   * @todo
   */
  declare let count1: number;
  ```

After obfuscation:

  ``` TypeScript
  declare let count: number;
  ```

Use `-keep-comments` to keep JSDoc comments in the declaration files.

>**Note**:
>
>Comments in the generated source files are all deleted by default, and no keep configuration is supported.

## -remove-log

Deletes calls to console.* statements, requiring that the return value of the console.* statement is not used. The effect is as follows:

  <!-- @[optionExample_removeLog1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // Before obfuscation:
  function add(a: number, b: number) {
    console.info("result", a + b);
    return a + b;
  }
  ```

  ``` TypeScript
  // After obfuscation:
  function add(a: number, b: number) {
      return a + b;
  }
  ```

If this option is configured, console.* statements in the following scenarios will be deleted.

1. Calls at the top level of a file.  

   <!-- @[optionExample_removeLog2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

   ``` TypeScript
   console.info("in tolevel");
   ```

2. Calls in code blocks.  

   <!-- @[optionExample_removeLog3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

   ``` TypeScript
   function foo1() {
     console.info('in block');
   }
   ```

3. Calls in modules or namespaces.  

   <!-- @[optionExample_removeLog4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

   ``` TypeScript
   // ArkGuardAbility.ts
   namespace ns {
     console.info('in ns');
   }
   ```

4. Calls in switch statements.  

   <!-- @[optionExample_removeLog5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

   ``` TypeScript
   function getDayName(day: number): string {
     switch (day) {
       case 1:
         console.info("Matched case 1: Monday");
         return "Monday";
       case 2:
         console.info("Matched case 2: Tuesday");
         return "Tuesday";
       default:
         console.error("No matching case for day:", day);
         return "Invalid date";
     }
   }
   ```

## -print-namecache

Saves the name cache to the specified file path **filepath**. The name cache contains the mapping between names before and after obfuscation. **filepath** is a required parameter and supports both relative and absolute paths. The starting position of a relative path is the current directory of the obfuscation configuration file. Use the `.json` suffix for the file name in the **filepath** parameter.

```text
-print-namecache
./customCache/nameCache.json
```

>**Note**:
>
>A new nameCache.json file is generated each time the project is fully built. Therefore, save a copy of this file when releasing a new version.

## -apply-namecache

Reuses the specified Name Cache File **filepath**. **filepath** is a required parameter and supports both Relative Path and absolute path. The starting position of a Relative Path is the current directory of the Obfuscation Configuration File. The file name in the **filepath** parameter must end with `.json`.

This option applies to incremental compilation. When enabled, names are obfuscated according to the cache file mapping. Newly added third-party dependency libraries may cause the obfuscation Whitelist to change, which in turn affects the obfuscation result. If the corresponding cache is not found, the name is obfuscated into a new random name.

```text
-apply-namecache
./customCache/nameCache.json
```

By default, DevEco Studio saves the cache file in the temporary cache directory and automatically applies it during incremental compilation.

Cache directory: build/default/cache/{...}/release/obfuscation.

## -print-kept-names

This option supports outputting the unobfuscated name list and the full whitelist, and supports configuring **filepath**. **filepath** is an optional parameter that supports only relative paths. The starting position of the relative path is the current directory of the obfuscation configuration file. The file name in the **filepath** parameter must end with `.json`.

Starting from API version 18, outputting the unobfuscated name list and the full whitelist is supported.

When the **filepath** parameter is omitted, the unobfuscated name list (keptNames.json) and the full whitelist (whitelist.json) are output to the cache path `build/default/cache/{...}/release/obfuscation` by default.

If the developer configures the **filepath** parameter, the unobfuscated name list is output to the path specified by the **filepath** parameter.

The whitelist collected during a full compilation process is divided into the following seven types:

(1) 'sdk': indicates system APIs.

(2) 'lang': indicates keywords in the language.

(3) 'conf': indicates the whitelist in the keep options configured by the user.

(4) 'struct': indicates properties in the struct of ArkUI.

(5) 'exported': Indicates the exported names and their properties.

(6) 'strProp': Indicates string properties.

(7) 'enum': Indicates the members in an enum.

Among them, the 'sdk' whitelist is output separately to the `systemApiCache.json` file under the cache path `build/default/cache/{...}/release/obfuscation/`, while whitelists of other types are all output to the `whitelist.json` file.

The unobfuscated name list (keptNames.json) contains unobfuscated names and the reasons why they are not obfuscated. The reasons include: name collision with the SDK whitelist, name collision with the language whitelist, name collision with the user-configured whitelist, name collision with the struct whitelist, name collision with the exported whitelist, name collision with the string property whitelist (when [String Property Obfuscation](#-enable-string-property-obfuscation) is not enabled), and name collision with the enum whitelist.

**Note the following when using this option:**

1. When compiling a HAR module with property obfuscation enabled, the 'enum' whitelist collects the member names in the enum.

   <!-- @[optionExample_printKeptNames1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

   ``` TypeScript
   enum Test1 {
     member1,
     member2
   }
   ```

    The enum whitelist content is ['member1', 'member2']. This is because the intermediate compilation artifact of HAR modules in earlier versions is a JS file, in which an enum type is converted into an immediately invoked function, and enum members are converted into a string property and a string constant. Therefore, to ensure normal functionality when property obfuscation is enabled, enum member names need to be collected into the whitelist. This behavior is still retained when compiling bytecode HAR modules of the new version.

2. When compiling a HAP/HSP/bytecode HAR module with property obfuscation enabled, when an enum member is initialized, the 'enum' whitelist collects the variable names contained in the initialization expression.

   <!-- @[optionExample_printKeptNames2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->     

   ``` TypeScript
   // ArkGuardAbility.ts
   let outdoor = 1;
   enum Test2 {
     member1,
     member2 = outdoor + member1 + 2
   }
   ```

    Among them, when compiling a HAP/HSP module, the enum whitelist content is ['outdoor', 'member1']; when compiling a bytecode HAR module, the enum whitelist content is ['outdoor', 'member1', 'member2'].

## -extra-options strip-language-default

The preset language whitelist for obfuscation **includes by default the names of DOM, WebWorker, ScriptHost, and other APIs in TypeScript system interfaces, as well as Web API names**. If properties in the developer's source code have the same names as these, the obfuscation tool keeps these properties.

If developers need to obfuscate this part of the code, they need to configure the `-extra-options strip-language-default` option.

This option is supported since API version 18.

Developers can determine the specific reduction scope of the APIs kept by default by the obfuscation tool in the following way:

Enable the `-print-kept-names` option, and compare the differences in the `lang` field content in the full whitelist (whitelist.json) when the `-extra-options strip-language-default` option is enabled and disabled. The difference is the specific reduction scope of the preset language whitelist.

## -extra-options strip-system-api-args

The system API whitelist used by the current obfuscation **includes local variable names in system APIs by default**, and the system API whitelist takes effect on local variables in developer source code by default. If a property in developer source code has the same name as a local variable in a system API, or a local variable in source code has the same name as an entry in the system API whitelist, the obfuscation tool keeps these property and local variable names.

To obfuscate this part of the code, configure the `-extra-options strip-system-api-args` option.

This option is supported since API version 18.

The ReservedLocalNames, ReservedPropertyNames, and ReservedGlobalNames fields in the system API whitelist file (systemApiCache.json) can be used to view the specific content of the system API whitelist. The system API whitelist file is located in the build/default/cache/{...}/release/obfuscation path under the module directory, and records the interface and property names in the SDK. Source code with the same names will not be obfuscated.

Developers can determine the specific reduction scope of the system whitelist in the following way:

Compare the content differences in the ReservedLocalNames and ReservedPropertyNames fields of the system API whitelist file (systemApiCache.json) when the `-extra-options strip-system-api-args` option is enabled and disabled. The difference is the specific reduction scope of the system whitelist. The content of the ReservedGlobalNames field does not change.

## -extra-options strip-not-compiled-module-name

The current obfuscation whitelist **includes all module names in the project by default**. If a file name in the developer's source code duplicates a module name, the obfuscation tool keeps these file names.

Developers can configure the `-extra-options strip-not-compiled-module-name` option to obfuscate files that share the same name as modules not involved in compilation.

This option is supported since API version 22.

After this option is enabled, only the names of compiled modules and their directly and indirectly dependent local source Har modules are added to the obfuscation whitelist, while the names of other modules are not kept.

**Use the -extra-options option as follows**:

Add the `-extra-options` prefix and the option in the obfuscation configuration file, with no other content between the prefix and the option. Enabling a single option or multiple options at the same time is supported.

- Use the -extra-options prefix to enable a single option in the following two ways:

  ```text
  # Method 1
  -extra-options
  strip-language-default

  # Method 2
  -extra-options strip-language-default
  ```

- Use the -extra-options prefix to enable multiple options simultaneously. There are five ways to use it:

  ```text
  # Method 1
  -extra-options strip-language-default, strip-system-api-args, strip-not-compiled-module-name

  # Method 2
  -extra-options strip-language-default strip-system-api-args strip-not-compiled-module-name

  # Method 3
  -extra-options
  strip-language-default strip-system-api-args strip-not-compiled-module-name

  # Method 4
  -extra-options
  strip-language-default
  strip-system-api-args
  strip-not-compiled-module-name

  # Method 5
  -extra-options strip-language-default
  -extra-options strip-system-api-args
  -extra-options strip-not-compiled-module-name
  ```

## -keep-parameter-names

Starting from API version 18, the parameter names of external interfaces in the declaration file can be kept. When this option is enabled, the following effects take place:

- For functions and member methods in classes, if the function or method name is not obfuscated, its parameter names are kept.

- For class constructors, if the class name is not obfuscated, the parameter names in the constructor are kept.

**Note the following when using this option:**

1. For parameter names in scenarios other than those described above (such as anonymous functions), they cannot be kept through this option.

2. Parameter names in source code files are still obfuscated and cannot be kept through this option.

## -enable-lib-obfuscation-options

When this switch is configured, the obfuscation options of dependency modules are merged into the obfuscation configuration of the current compilation module.

This option is supported since API version 18.

The obfuscation configuration is divided into [Obfuscation Options](#obfuscation-option-summary) and Keep Options:

- **By default**, the effective obfuscation configuration is the merged result of the current compilation module's obfuscation configuration and the dependency modules' keep options.  

- **After this switch is enabled**, the effective obfuscation configuration is the merged result of the current compilation module's obfuscation configuration and the dependency modules' obfuscation configurations.

For the obfuscation rule merging logic, see [Obfuscation Rule Merging Policy](./source-obfuscation.md).

## -use-keep-in-source

Starting from API version 19, the following two comment markers in `.ts` and `.ets` source code can be used to add names to the whitelist. They are not supported in declaration files.

`// @KeepSymbol`: used to mark names that need to be kept. It is usually written on the line above the code, indicating that the name will not be obfuscated at compile time.

`// @KeepAsConsumer`: used to mark names that need to be kept. It is usually written on the line above the code, indicating that the name will not be obfuscated at compile time. In HAR/HSP modules, names marked with @KeepAsConsumer are also generated in obfuscation.txt. In HAP modules, @KeepAsConsumer has the same effect as @KeepSymbol.

> **Note**:
>
> Both markers above are comments, and "//" must not be removed.

### Syntax Scenarios Supported by Comment Markers

The following uses `// @KeepSymbol` as an example. The scenarios supported by `// @KeepAsConsumer` are the same as those supported by `// @KeepSymbol`.

1. Class

    The following syntax in a class can be marked:

    - Class declaration

    - Constructor

    - Fields and methods

    <!-- @[optionExample_useKeepInSource1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

    ``` TypeScript
    // Keep the class name and all member names
    // @KeepSymbol
    class MyClass02 {
      prop01: string = "prop"; // MyClass02 and prop01 will not be obfuscated
    }
    
    // Keep the class name through the constructor
    class MyClass03 {
      prop02: string = "prop";
      // @KeepSymbol
      constructor() {}; // MyClass03 will not be obfuscated.
    }
    
    // Keep the class name and the specified field and method names. MyClass04, prop03_1, and method03_2 in the class will not be obfuscated.
    class MyClass04 {
      // @KeepSymbol
      prop03_1: string = "prop";
      prop03_2: number = 1;
      constructor() {};
    
      method03_1(): void {};
      // @KeepSymbol
      method03_2(): void {};
    }
    ```

2. Interface

    The following syntax in an interface can be marked:

    - Interface declaration

    - Fields and methods

    <!-- @[optionExample_useKeepInSource2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

    ``` TypeScript
    // Keep the interface name and all member names. MyInterface01, name01, and foo01 will not be obfuscated.
    // @KeepSymbol
    interface MyInterface01 {
      name01: string;
      foo01(): void;
    }
    
    // Keep the interface name and the specified field and method names. MyInterface02 and name02 will not be obfuscated.
    interface MyInterface02 {
      // @KeepSymbol
      name02: string;
      foo02(): void;
    }
    ```

3. Enumerated value

    The following syntax in an enum can be marked:

    - Enum declaration

    - Enum members

    <!-- @[optionExample_useKeepInSource3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

    ``` TypeScript
    // Keep the enum name and all member names. Color01, RED01, and BLUE01 will not be obfuscated.
    // @KeepSymbol
    enum Color01 {
      RED01,
      BLUE01
    }
    
    // Keep the enum member names specified by the enum name.
    enum Color02 {
      RED02,
      // @KeepSymbol
      BLUE02 // Color02 and BLUE02 will not be obfuscated.
    }
    ```

4. Functions

    Supports marking function names.

    <!-- @[optionExample_useKeepInSource4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

    ``` TypeScript
    // Keep the function name. MyAdd will not be obfuscated.
    // @KeepSymbol
    function MyAdd(a: number, b:number): number {
      return a + b;
    }
    ```

5. Namespace

    Supports marking namespace names.

    <!-- @[optionExample_useKeepInSource5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

    ``` TypeScript
    // Keep the namespace name and the names of its directly exported members. MyNameSpace and foo will not be obfuscated.
    // @KeepSymbol
    namespace MyNameSpace {
      export function foo(){};
      function bar(){};
    }
    ```

6. Global variables

    Marking global variables is supported, but marking local variables is not.

    <!-- @[optionExample_useKeepInSource6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->     

    ``` TypeScript
    // Keep the marked variable name. myVal will not be obfuscated.
    // @KeepSymbol
    const myVal = 1;
    ```

7. Annotations

    Only marking and keeping annotation declarations is supported. Marking annotation members is ineffective, and annotation members themselves are not obfuscated.

    Starting from API version 20, marking annotation declarations is supported.

    <!-- @[etsOptionExample_useKeepInSource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) -->    

    ``` TypeScript
    // Keep the marked annotation declaration. MyAnnotation will not be obfuscated.
    // @KeepSymbol
    @interface MyAnnotation2 {
      // Marking annotation members is ineffective. authorName will not be collected into the whitelist.
      // @KeepSymbol
      authorName: string;
      revision: number = 1;
    }
    ```

### Whitelist Addition Rules for Comment Markers

Marked names are added to the obfuscation whitelist according to the following rules. Names kept by `// @KeepAsConsumer` are also generated into the [obfuscation.txt](./source-obfuscation-guide.md) file.

* If the name is in the top-level scope or is directly exported, it is added to -keep-global-name.

* If the name is directly exported, it is also added to -keep-property-name.

* If the name is a property, it is also added to -keep-property-name.

* Local variable names are not added to the whitelist (they are not kept).

  <!-- @[optionExample_useKeepInSource7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->

  ``` TypeScript
  // @KeepAsConsumer
  export class MyClass05 {
    prop01: string = "prop";
  }
  ```

  In the example above, MyClass05 is added to -keep-global-name and -keep-property-name, and `prop01` is added to -keep-property-name. Meanwhile, this rule is also written into the `obfuscation.txt` file.

### Unsupported Syntax Scenarios for Comment Markers

String properties, numeric properties, and computed properties are not supported.

<!-- @[optionExample_useKeepInSource8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

``` TypeScript
// ArkGuardAbility.ts
const myMethodName = "myMethod";

// 11, aa, and myMethod will not be collected into the whitelist.
class MyClass06 {
  // @KeepSymbol
  11:11;
  // @KeepSymbol
  'aa':'aa';
  // @KeepSymbol
  [myMethodName](){}
}

// RED will not be collected into the whitelist.
enum MyEnum {
  // @KeepSymbol
  'RED',
  BLUE
}
```

## -keep-object-props

Starting from API version 23, the -keep-object-props configuration option is supported to keep property names and string property names in object literals. The usage is as follows:

- When only property obfuscation (-enable-property-obfuscation) is enabled, after configuring the keep object literals (-keep-object-props) option, the property names in object literals are collected into the whitelist and will not be obfuscated.

- When both property obfuscation (-enable-property-obfuscation) and string property obfuscation (-enable-string-property-obfuscation) are enabled, after configuring the keep object literals (-keep-object-props) option, the property names and string property names in object literals are collected into the whitelist and will not be obfuscated.

>**Note**:
>
> The -keep-object-props option takes effect only when property obfuscation is enabled, or when both property obfuscation and string property obfuscation are enabled. Otherwise, this option is invalid.

**Supported Scenarios**

Keeping property names and string property names in object literals is supported.

```typescript
// example.ts
const propertyObj = {
    propertyKey1: 'value',
    propertyKey2: {
        propertyKey3: 'value'
    }
};
const stringPropertyObj = {
    'stringPropertyKey1': 'Alice',
    'stringPropertyKey2': {
        'stringPropertyKey3': 'additional data'
    }
};
```

1. When property obfuscation is enabled, if the -keep-object-props option is configured, the property names in object literals will not be obfuscated.

   The obfuscation configuration option file obfuscation-rules.txt is as follows:

   ```text
   -keep-object-props
   -enable-property-obfuscation
   ```

   After enabling the obfuscation options in the obfuscation-rules.txt configuration file above, the property names propertyKey1, propertyKey2, and propertyKey3 in the sample code are collected into the whitelist and will not be obfuscated.

2. When property obfuscation and string property obfuscation are enabled, if the -keep-object-props option is configured, the property names and string property names in object literals will not be obfuscated.

   The obfuscation configuration file obfuscation-rules.txt is as follows:

   ```text
   -keep-object-props
   -enable-property-obfuscation
   -enable-string-property-obfuscation
   ```

   After the obfuscation options in the obfuscation-rules.txt configuration file above are enabled, the property names propertyKey1, propertyKey2, and propertyKey3, as well as the string property names stringPropertyKey1, stringPropertyKey2, and stringPropertyKey3 in the sample code, will be collected into the whitelist and will not be obfuscated.

**Unsupported Scenarios**

Scenarios where the property name is not in an object literal are not supported.

```typescript
// example.ts
// Scenarios where -keep-object-props does not take effect: typeLiteral1, typeLiteral2, typeLiteral3, typeLiteral4, and typeLiteral5 are not properties in an object literal. When property obfuscation is enabled, or when both property obfuscation and string property obfuscation are enabled, they will still be obfuscated even if the -keep-object-props option is enabled.
interface TypeLiteralDemo {
  typeLiteral1: {
    typeLiteral2: number,
    'typeLiteral3': string
  },
  typeLiteral4: string,
  'typeLiteral5': string
}

// Scenarios where -keep-object-props does not take effect: Symbol.iterator, dynamic, and Property are all complex computed properties. When property obfuscation is enabled, or when both property obfuscation and string property obfuscation are enabled, they will not be obfuscated regardless of whether the -keep-object-props option is enabled.
const complexComputedPropertyObj = {
  [Symbol.iterator]: 'value',
  ["dynamic" + "Property"]: 'value'
}
```

## -remove-nosideeffects-calls

Starting from API version 23, deletion of method calls with specified names is supported, provided that the return value of the method call is not used. This feature is suitable for scenarios such as deleting custom log method calls.

The supported method call forms are as follows:

1. Direct call: method, matches method().

2. Dot call: A.B, matches A.B().

3. Bracket call: A["B"], matches A["B"]\(\).

4. Nested call: A.B["method"], matches A.B["method"]\(\).

5. Wildcard matching: performs pattern matching through name-type wildcards, such as *.log, which matches log() of any object.

**Note the following when using this option:**

1. When using this option to delete method calls, the side effects inside them are not analyzed. Ensure that the deleted method calls do not affect application functionality.

2. The configuration item must match the complete name at the actual call site in the source code, not the name at the declaration site.

   For example, in the following example, the configuration item `MyLog.debug` is not the name at the call site, so `Log.debug()` will not be removed:  

   ```text
   // obfuscation-rules.txt or consumer-rules.txt:
   -remove-nosideeffects-calls
   MyLog.debug
   ```

   ``` TypeScript
   // a.ts
   export class MyLog {
     public static debug(message: string) {
       console.info(message);
     }
   }

   // b.ts
   import { MyLog as Log } from './a'

   Log.debug("this is alias"); 
   ```

3. Configuration items can be separated by commas, spaces, or line breaks.

In the obfuscation configuration file obfuscation-rules.txt or consumer-rules.txt:

```text
-remove-nosideeffects-calls
logger
Log.debug*
example["log"].info
```

Based on the above configuration, method call statements in the following scenarios will be removed:  

1. Calls at the top level of a file.

   ``` TypeScript
   function logger(msg: string) {
     console.info(msg);
   }

   logger("in top level"); // After obfuscation, this method call will be removed
   ```

2. Calls in a code block.

   ``` TypeScript
   class Log {
     public static debugBlock(msg: string) {
       console.info(msg);
     }
   }

   function foo() {
     Log.debugBlock("in block"); // After obfuscation, this method call will be removed
   }
   ```

3. Calls in a module or namespace.

   ``` TypeScript
   // example.ts
   class Log {
     public static debugNamespace(msg: string) {
       console.info(msg);
     }
   }

   namespace ns {
     Log.debugNamespace("in namespace"); // After obfuscation, this method call is removed.
   }
   ```

4. Calls in a switch statement.

   ``` TypeScript
   interface Logger {
     info: (msg: string, res?: number) => void;
   }

   const logFunc: Logger = {
     info: (msg: string, res?: number): void => {
       console.info(msg, res);
     }
   }

   const example: Record<string, Logger> = {
     ["log"]: logFunc
   }

   function getDayName(day: number): string {
     switch (day) {
       case 1:
         example["log"].info("Matched case 1: Monday"); // After obfuscation, this method call is removed.
         return "Monday";
       case 2:
         example["log"].info("Matched case 2: Tuesday"); // After obfuscation, this method call is removed.
         return "Tuesday";
       default:
         example["log"].info("No matching case for day:", day); // After obfuscation, this method call is removed.
         return "Invalid date";
     }
   }
   ```