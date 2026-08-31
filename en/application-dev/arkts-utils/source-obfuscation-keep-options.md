# ArkGuard Obfuscation Keep Options

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=76413f655ee0ef537da838554c380a0edb4adb50 translatedAt=2026-08-31T12:42:27.755Z pushedAt=2026-08-31T15:15:40.467Z -->

Starting from API version 10, after obfuscation is enabled, methods, properties, or paths in the code will be obfuscated. However, at runtime, accessing obfuscated methods, properties, or paths by their original names before obfuscation may cause functionality to fail. Therefore, you need to configure the corresponding keep options based on different scenarios.

When troubleshooting scenarios and configuring fields, it is recommended to use [Obfuscation Assistant to configure keep options](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-build-obfuscation#section19439175917123) to quickly identify the keep options and trustlist fields that need to be configured.

## Keep Option Summary

| Function | Option | Initial API Version |
| --- | --- | --- |
| Specified keep property name | [`-keep-property-name`](#-keep-property-name) | 10 |
| Specified keep top-level scope or import/export element name | [`-keep-global-name`](#-keep-global-name) | 10 |
| Specified keep file/folder name | [`-keep-file-name`](#-keep-file-name) | 10 |
| Specified keep comment | [`-keep-comments`](#-keep-comments) | 12 |
| Specified keep all names in the declaration file | [`-keep-dts`](#-keep-dts) | 12 |
| Specified keep all names in the source code file | [`-keep`](#-keep) | 12 |
| Name and path keep options support wildcards | [`Wildcards Supported by Keep Options`](#keep-options-support-wildcards)  | 12 |
| Exclude files at the specified path during code compaction | [`-keep-uncompact`](#-keep-uncompact) | 26.0.0 |

## -keep-property-name

Specifies the property names to keep, and supports the use of [Name Wildcard](#name-wildcard). Configure it as follows to keep the properties named `firstName` and `lastName`:

```txt
-keep-property-name
firstName
lastName
```

**Note the following when using this option:**

1. This option takes effect when -enable-property-obfuscation is enabled.

2. The property trustlist applies globally. That is, if multiple properties with the same name appear in the code, none of them will be obfuscated as long as their names match those in the `-keep-property-name` configuration trustlist.

**Property names that require manual trustlist configuration:**

1. If object properties are defined in the code through string concatenation, variable access, or the defineProperty method, these property names should be kept.

    <!-- @[jsOptionExample_keepPropertyName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.js) -->   

    ``` JavaScript
    // ArkGuardAbility.js
    var obj = {x0: '0', x1: '1', x2: '2'};
    for (var i = 0; i <= 2; i++) {
        console.info(obj['x' + i]); // x0, x1, x2 should be kept
    }
    
    Object.defineProperty(obj, 'y', {}); // y should be kept
    Object.getOwnPropertyDescriptor(obj, 'y'); // y should be kept
    console.info(obj.y);
    
    obj.s1 = 'a';
    let key = 's1';
    console.info(obj[key]); // The variable value s1 corresponding to key should be kept.
    
    obj.t1 = 'b';
    console.info(obj['t' + '1']); // t1 should be kept.
    ```

For property calls in the form of string constants as shown below, you can selectively keep them:

    <!-- @[optionExample_keepPropertyName1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->      

    ``` TypeScript
    // Obfuscation configuration:
    // -enable-property-obfuscation
    // -enable-string-property-obfuscation
    
    // ArkGuardAbility.ts
    var obj2 = {t:'1', m:'2'};
    obj2.t = 'a';
    console.info(obj2['t']); // At this point, 't' will be correctly obfuscated, and t can be selectively kept.
    
    obj2['m'] = 'b';
    console.info(obj2['m']); // At this point, 'm' will be correctly obfuscated, and m can be selectively kept.
    ```

2. For scenarios involving property names of indirectly or directly exported classes or objects, if problems occur after obfuscation, you can use [-keep-property-name](#-keep-property-name) to keep these property names.

      <!-- @[optionExample_keepPropertyName2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->    

      ``` TypeScript
      // Indirectly export MyClass07
      class MyClass07 {
        greet() {}
      }
      let alias = new MyClass07();
      export { alias };
      
      // Directly export MyClass08
      export class MyClass08 {
        exampleName: 'jack'
        exampleAge: 100
      }
      ```

3. When using APIs of a so library (such as addNum in the example) in ArkTS/TS/JS files, you need to manually keep the API names.

    <!-- @[dtsOptionExample_keepPropertyName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/cpp/types/libentry/Index.d.ts) -->         

    ``` TypeScript
    // src/main/cpp/types/libentry/Index.d.ts
    export const addNum: (a: number, b: number) => number;
    ```

    <!-- @[etsOptionExample_keepPropertyName1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) -->        

    ``` TypeScript
    // ArkGuardAbility.ets
    import testNapi from 'libentry.so';
    // ...
    testNapi.addNum(2, 3); // addNum needs to be kept. Example: -keep-property-name addNum
    ```

4. When parsing JSON data and serializing objects, keep the fields that are used.

    ```json
    {
      "jsonProperty": "value",
      "otherProperty": "value2"
    }
    ```

    <!-- @[optionExample_keepPropertyName3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->     

    ``` TypeScript
    import jsonData from './ImportJson.json';
    // ...
    let jsonProp = jsonData.jsonProperty; // jsonProperty should be kept
    
    class JsonTest {
      prop1: string = '';
      prop2: number = 0
    }
    
    let obj = new JsonTest();
    const jsonStr = JSON.stringify(obj); // prop1 and prop2 will be obfuscated and should be kept
    ```

5. Manually keep the database-related fields that are used. For example, the properties in the database key-value pair type (ValuesBucket):

    <!-- @[optionExample_keepPropertyName4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->      

    ``` TypeScript
    import { ValuesBucket } from '@kit.ArkData';
    // ...
    const valueBucket: ValuesBucket = {
      ID1: 'ID1', // ID1 should be kept
      NAME1: 'jack', // NAME1 should be kept
      AGE1: 20, // AGE1 should be kept
      SALARY1: 100 // SALARY1 should be kept
    }
    ```

6. When custom decorators in the source code modify member variables, member methods, and parameters, and the intermediate product compiled from the source code is a js file (for example, when compiling release source code HAR or the source code contains @ts-ignore or @ts-nocheck), the names of the member variables/member methods where these decorators are located need to be kept. This is because when advanced TS syntax features are converted to standard js syntax, the names of the member variables/member methods where the above decorators are located are hardcoded as string constants.

    <!-- @[optionExample_keepPropertyName5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->      

    ``` TypeScript
    function CustomDecorator(target: Object, propertyKey: string) {}
    function MethodDecorator(target: Object, propertyKey: string, descriptor: PropertyDescriptor) {}
    function ParamDecorator(target: Object, propertyKey: string, parameterIndex: number) {}
    
    class A {
      // 1. Member variable decorator
      @CustomDecorator
      propertyName1: string = ""   // propertyName1 needs to be kept
      // 2. Member method decorator
      @MethodDecorator
      methodName1() {} // methodName1 needs to be kept
      // 3. Method parameter decorator
      methodName2(@ParamDecorator param: string): void {} // methodName2 needs to be kept
    }
    ```

7. Fields related to data requests that are used need to be kept manually. For example, fields passed to the data requester need to be kept manually:

    <!-- @[etsOptionExample_keepPropertyName2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) -->      

    ``` TypeScript
    // ArkGuardAbility.ets
    import { UIAbility } from '@kit.AbilityKit';
    import { http } from '@kit.NetworkKit';
    // ...
    export default class EntryAbility extends UIAbility {
      onForeground(): void {
        let httpRequest = http.createHttp();
        httpRequest.request('https://www.example/Login',
          {
            method: http.RequestMethod.POST,
            header: { 'Content-Type': 'application/json' },
            extraData: { usernameTest: 'test1', passwordTest: 'test2'}, // usernameTest and passwordTest need to be kept
          })
      }
    }
    ```

8. Numeric literal properties that are used need to be kept manually.

    <!-- @[optionExample_keepPropertyName6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->       

    ``` TypeScript
    class MyClass09 {
      123 = 'numeric-prop'; // Numeric literal property
      [456] = 'computed'; // Number in the computed property
      method() {
        console.info(this[123]); // 123 and 456 need to be kept
        console.info(this[456]);
      }
    }
    ```

## -keep-global-name

Specifies the names of top-level scopes and imported and exported elements to keep. It supports the use of [Name Wildcard](#name-wildcard). The configuration is as follows:

```text
-keep-global-name
Person
printPersonName
```

Names exported from a `namespace` can also be kept through the `-keep-global-name` option.

<!-- @[optionExample_keepGlobalName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->      

``` TypeScript
// ArkGuardAbility.ts
export namespace Ns {
  export const myAge = 18 // -keep-global-name myAge // Keep the variable myAge.
  export function myFunc() {} // -keep-global-name myFunc // Keep the function myFunc.
}
```

**Note the following when using this option:**

1. This option takes effect when -enable-toplevel-obfuscation or -enable-export-obfuscation is enabled.

2. The trustlist specified by [-keep-global-name](#-keep-global-name) applies globally. That is, if multiple top-level scope names or exported names appear in the code, any name that matches the trustlist configured by `-keep-global-name` will not be obfuscated.

**Top-level scope names that require manual trustlist configuration:**

When importing APIs from a so library using named imports, if both the `-enable-toplevel-obfuscation` and `-enable-export-obfuscation` options are enabled, you need to manually keep the API names.

<!-- @[dtsOptionExample_keepGlobalName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/cpp/types/libentry/Index.d.ts) -->         

``` TypeScript
// src/main/cpp/types/libentry/Index.d.ts
declare function testNapi2(): void;
declare function testNapi3(): void;
```

<!-- @[etsOptionExample_keepGlobalName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ets) -->        

``` TypeScript
// ArkGuardAbility.ets
import { testNapi2, testNapi3 as myNapi } from 'libentry.so'; // testNapi2 and testNapi3 should be kept
// ...
testNapi2();
myNapi();
```

## -keep-file-name

Specifies the file or folder name to keep (no file extension required), and supports the use of [Name Wildcard](#name-wildcard).

Taking the file path "utils/file.ets" as an example, the method for configuring the trustlist is as follows:

```text
-keep-file-name
utils
file
```

**Note the following when using this option:**

1. This option takes effect when -enable-filename-obfuscation is enabled.

2. The trustlist specified by `-keep-file-name` applies globally. That is, files or folders at different levels will not be obfuscated as long as their names are the same as the trustlist names configured by `-keep-file-name`.

3. Path Wildcard is not supported.

   ```text
   # This notation keeps only this path; the names of files and folders under the pages directory will still be obfuscated.
   -keep-file-name
   ./src/main/ets/components/pages/**
   ```

**File names that require manual trustlist configuration:**

1. When using `require` to import a file path, since `ArkTS` does not support [CommonJS module](../arkts-utils/module-principle.md#commonjs-module) syntax, the file path imported by `require` in this case should be kept.

    <!-- @[jsOptionExample_keepFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.js) -->       

    ``` JavaScript
    // ArkGuardAbility.js
    const module1 = require('./RequireFile'); // RequireFile should be kept.
    ```

2. For the path name of a dynamic import, since it is impossible to identify whether the parameter in the `import` function is a path, the path name of the dynamic import should be kept in this case.

    <!-- @[testOptionExample_keepFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/DynamicImportFile.ts) -->        

    ``` TypeScript
    // DynamicImportFile.ts
    export function foo () {}
    ```

    <!-- @[optionExample_keepFileName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->        

    ``` TypeScript
    // ArkGuardAbility.ts
    const moduleName = './DynamicImportFile'; // The path name DynamicImportFile corresponding to moduleName should be kept.
    async function func2() {
      const modules = await import(moduleName);
      const result = modules.foo();
    }
    ```

3. For API version 19 and earlier, when using [Navigation cross-package routing](../ui/arkts-navigation-cross-package.md) for route navigation, the path passed to the dynamic route should be kept. Dynamic routing provides two modes: the system route table and the custom route table:

    If the custom route table is used for navigation, the configuration trustlist is configured in the same way as the second dynamic reference scenario.

    If the system route table is used for navigation, the path corresponding to the `pageSourceFile` field in the `resources/base/profile/route_map.json` file under the module must be added to the trustlist.

    For API version 20 and later, manual trustlist configuration is no longer required.

      ```json
      {
        "routerMap": [
          {
            "name": "PageOne",
            "pageSourceFile": "src/main/ets/pages/directory/PageOne.ets",
            "buildFunction": "PageOneBuilder",
            "data": {
              "description" : "this is PageOne"
            }
          }
        ]
      }
      ```

4. For API version 19 and earlier, when using the [application startup framework AppStartup](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-startup), the paths of the startup parameter configuration file and the startup task file should be kept. These paths are configured in the `resources/base/profile/startup_config.json` file of this module, corresponding to the `configEntry` field and the `srcEntry` field of the `startupTasks` object, respectively.

   For API version 20 and later, manual trustlist configuration is no longer required.

   The following is an example of the `startup_config.json` file:

    ```json
    {
      "startupTasks": [
        {
          "name": "StartupTask_001",
          "srcEntry": "./ets/startup/StartupTask_001.ets",
          "dependencies": [
            "StartupTask_002"
          ],
          "runOnThread": "taskPool",
          "waitOnMainThread": false
        },
        {
          "name": "StartupTask_002",
          "srcEntry": "./ets/startup/StartupTask_002.ets",
          "runOnThread": "taskPool",
          "waitOnMainThread": false
        }
      ],
      "configEntry": "./ets/startup/StartupConfig.ets"
    }
    ```

    The Configuration trustlist is configured as follows:

    ```text
    -keep-file-name
    # The startup task file paths are: "./ets/startup/StartupTask_001.ets" and "./ets/startup/StartupTask_002.ets".
    startup
    StartupTask_001
    StartupTask_002

    # The startup parameter configuration file path is: "./ets/startup/StartupConfig.ets".
    StartupConfig
    ```

5. When using the routing jump method provided by a third-party library, if the file name obfuscation rule is enabled, the file path will be obfuscated, causing the jump to fail. Therefore, all routing jump paths must be configured under `-keep-file-name` to prevent the file paths from being obfuscated.

## -keep-comments

Keeps the JsDoc comments above class, function, namespace, enum, struct, interface, module, type, and properties in the declaration file generated during compilation. It supports the use of [Name Wildcard](#name-wildcard). For example, to keep the JsDoc comment above the Human class in the declaration file, you can use the following configuration:

```text
-keep-comments
Human
```

**When using this option, note the following:**

1. This option takes effect when -remove-comments is enabled.

2. When the names of class, function, namespace, enum, struct, interface, module, type, and properties in the declaration file generated during compilation are obfuscated, the JsDoc comments above these elements cannot be kept through `-keep-comments`. For example, when exportClass is configured in `-keep-comments`, if the exportClass class name is obfuscated, its JsDoc comment cannot be kept.

   <!-- @[optionExample_keepComments](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSCompilationToolchain/ArkGuardForSourceCodeObfuscation/ArkGuardObfuscationAbility/entry/src/main/ets/arkguardability/ArkGuardAbility.ts) -->         

   ``` TypeScript
   /**
    * @class exportClass
    */
   export class exportClass {}
   ```

## -keep-dts

Names (such as variable names, class names, and property names) in the `.d.ts` file at the specified path `filepath` will be added to the `-keep-global-name` and `-keep-property-name` trustlists. Ensure that `filepath` is an absolute path. It can also be specified as a directory. If it is specified as a directory, all names in all `.d.ts` files under that directory will be kept.

## -keep

Keeps all names (such as variable names, class names, and property names) in the specified relative path *filepath* from being obfuscated. *filepath* can be a file or a folder. If it is a folder, the files in the folder and its subfolders are not obfuscated.

*filepath* supports only relative paths. `./` and `../` are relative to the directory where the obfuscation configuration file is located. [Path Wildcard](#path-wildcard) is supported.

```text
-keep
./src/main/ets/fileName.ts   // Names in fileName.ts are not obfuscated.
../folder                    // Names in the files and subfolders under the folder directory are not obfuscated.
../oh_modules/json5          // Names in all files of the referenced third-party library json5 are not obfuscated.
```

**How to Keep a Remote HAR Package in a Module**

**Method 1**: Specify the specific path of the remote `HAR` package in the module-level `oh_modules` (this path is a symbolic link path, and the real path is the file path in the project-level `oh_modules`). When configuring the path in the module-level `oh_modules` as a trustlist, you must specify the package name or a directory after it to correctly link to the real directory path. Therefore, you cannot configure only the parent directory name of the `HAR` package.

```text
// Example
-keep
./oh_modules/harName1         // Names in all files and subfolders under the harName1 directory are not obfuscated.
./oh_modules/harName1/src     // Names in all files and subfolders under the src directory are not obfuscated.
./oh_modules/folder/harName2  // Names in all files and subfolders under the harName2 directory are not obfuscated.

// Counterexample
-keep
./oh_modules                  // When keeping HAR packages in module-level oh_modules, configuring the parent directory name of the HAR package is not supported.
```

**Method 2**: Specify the specific path of the remote `HAR` package in the project-level `oh_modules`. The file paths in the project-level `oh_modules` are all real paths and can be configured directly.

```text
-keep
../oh_modules                  // Names in all files and subfolders under the project-level oh_modules directory are not obfuscated.
../oh_modules/harName3          // Names in all files and subfolders under the harName3 directory are not obfuscated.
```

The directory structures of module-level `oh_modules` and project-level `oh_modules` in `DevEco Studio` are shown in the following figure:


**Note the following when using this option:**

1. For a file kept using `-keep filepath`, the exported names and their properties in the files on its dependency chain are also kept.

2. This feature does not affect the filename obfuscation feature `-enable-filename-obfuscation`.

3. When a file is kept using the -keep rule, the code in that file is not obfuscated. However, when a property name in that file is referenced in other files, it may still be obfuscated. In this case, refer to [Common Cases of the -keep Rule](./source-obfuscation-questions.md) to resolve the issue.

## -keep-uncompact

Starting from API version 26.0.0, you can use `-keep-uncompact` to specify that source code under a relative path **does not participate in** code compaction.

**When using this option, note the following:**

1. This option takes effect only after -compact is enabled. If `-compact` is not enabled, the configuration does not take effect.

2. The configured path supports only relative paths. Both `./` and `../` are relative to the directory where the obfuscation configuration file is located. If the configured path is a folder, files in the folder and its subfolders are not compacted.

3. When the configured path points to a remote third-party package (that is, the `oh_modules` directory), specify its real path in the **project-level** `oh_modules` (consistent with method 2 of keeping remote HAP packages in [`-keep`](#-keep)) to ensure correct path parsing.

```text
-compact
-keep-uncompact
./src/main/ets/example/FileA.ets
./src/main/ets/example/folder
../oh_modules/somePackage/src
```

## Wildcards Supported by Keep Options

### Name Wildcard

Name wildcards are used as follows:

| Wildcard | Meaning | Example |
| -------- | ---------------------- | ------------------------------------------ |
| ? | Match any single character | "AB?" can match "ABC", but cannot match "AB". |
| \* | Match any number of any characters | "\*AB\*" can match "AB", "aABb", "cAB", "ABc", etc. |

**Example**:

Keep all property names starting with a:

```text
-keep-property-name
a*
```

Keep all single-character property names:

```text
-keep-property-name
?
```

Keep all property names:

```text
-keep-property-name
*
```

### Path Wildcard

Path wildcards are used as follows:

| Wildcard | Meaning                                                                     | Example                                              |
| ------ | ------------------------------------------------------------------------ | ------------------------------------------------- |
| ?     | Matches any single character except the path separator `/`.                                      | "../a?" can match "../ab", but cannot match "../a/".         |
| \*      | Matches any number of arbitrary characters, excluding the path separator `/`.                                | "../a*/c" can match "../ab/c", but cannot match "../ab/d/s/c". |
| \*\*   | Matches any number of arbitrary characters.                                                   | "../a**/c" can match "../ab/c", and can also match "../ab/d/s/c".  |
| !      | Represents negation. It can only be written at the beginning of a path to exclude an existing case in the user-configured trustlist. | "!../a/b/c.ets" represents matching paths other than "../a/b/c.ets".           |

**Usage example**:

Indicates that the c.ets files in all folders (excluding subfolders) under the path ../a/b/ will not be obfuscated:

```text
-keep
../a/b/*/c.ets
```

Indicates that the c.ets files in all folders (including subfolders) under the path ../a/b/ will not be obfuscated:

```text
-keep
../a/b/**/c.ets
```

Indicates that all files except c.ets under the path ../a/b/ will not be obfuscated. Here, `!` cannot be used alone and can only be used to exclude existing cases in the trustlist:

```text
-keep
../a/b/
!../a/b/c.ets
```

Indicates that all files (excluding subfolders) under the path ../a/ will not be obfuscated:

```text
-keep
../a/*
```

Indicates that all files in all folders (including subfolders) under the path ../a/ will not be obfuscated:

```text
-keep
../a/**
```

Indicates that all files in the module will not be obfuscated:

```text
-keep
./**
```

**Note the following when using wildcards:**

1. The preceding options do not support using the wildcards `*`, `?`, and `!` for other meanings.

    ```text
    class A {
      '*'= 1
    }

    -keep-property-name
    *
    ```

    In this case, `*` means matching any number of any characters. The configuration effect is that all property names will not be obfuscated, rather than only the `*` property not being obfuscated.

2. The -keep option allows only the `/` path format, and does not support `\` or `\\`.