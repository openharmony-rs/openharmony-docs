# Modularization FAQ

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @yao_dashuai-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e4e0aedb5d411cb2875cc6d281d8bd0dc18ac58c translatedAt=2026-08-31T12:35:56.569Z pushedAt=2026-08-31T14:42:59.260Z -->

## Object is not initialized

**Symptom**

The application reports an error at runtime: "Object is not initialized", which prevents the application from running normally. The Object in the specific error message is the variable actually used, such as "a is not initialized".

**Possible Causes**

A circular dependency exists between modules, causing the variable to be accessed before its initialization is complete.

Circular dependency refers to the problem where two or more modules reference each other, forming a circular reference relationship. During module loading, if it is not handled properly, it may cause exceptions such as uninitialized variables.

The occurrence of circular dependency problems is closely related to the module loading order and execution timing. Understanding its principles helps quickly locate and resolve the problem.

1. Module loading order.

   According to the ECMA specification, the execution order of modules is depth-first traversal loading.

   Assuming the application has a loading link A->B->C, ArkTS modularization executes file C first, then file B, and finally file A, with the execution order being C->B->A.

2. Execution flow of circular dependency.

   If the application has a loading link A->B->A, according to the depth-first traversal execution order, the execution flow first marks the state of A as loading, then loads B, marks the state of B as loading, then loads A. Since file A is already marked as loading, according to the specification definition, a module recognized as loading is returned directly, so file B is executed first.

3. Why do some circular dependencies have no impact, while others cause a crash?

   From the above analysis, file B depends on variables from file A, but because file B executes first, if the variables imported from file A are not used in the global scope or class static context, file B executes normally. Conversely, if file B uses variables from file A in the global scope, or when instantiating a class or through other methods, the variables from file A are accessed during file execution. Since the variables in file A have not been initialized yet, a crash with "Object is not initialized" occurs, meaning the circular dependency causes the variables to be uninitialized.

**Solution**

1. Enable the module error detection enhancement switch, reproduce the issue, and locate the error.

   ```bash
   hdc shell param set persist.ark.properties 0x2000105c
   ```

2. Handle the error. If the error still shows "Object is not initialized", use the module loading link debugging tool to check for circular dependency issues.

3. Analyze the module loading link to locate the circular dependency relationship between modules.

   By enabling the module loading link debugging tool, you can observe the module loading link when the exception occurs. At this point, the top of the stack is module B. Combined with the error information, it can be inferred that module B attempts to access variables from module A, thereby deducing the A->B->A circular dependency link.

4. Refactor the code structure to eliminate the circular dependency.

   By modifying the dependency relationships between modules, ensure that there are no circular references. Common methods include:

   - Extract common dependencies into an independent module

   - Adjust the module import order

   - Use dependency injection or other methods to decouple module relationships

**Code Example**

The following example contains a loading link A->B->A. During execution, the exception "a is not initialized" occurs.

``` typescript
// A.ets
import { Animal } from './B'

export let a = "this is A";
export function A() {
  return new Animal();
}

// B.ets
import { a } from './A'

export class Animal {
  static {
    console.info("this is in class");
    let str = a; // Error message: a is not initialized
  }
}
```

By enabling the module loading link debugging tool, you can view the module loading link when the exception occurs:

```text
ModuleImportStack:
#0 &entry/src/main/ets/pages/B&
#1 &entry/src/main/ets/pages/A&
#2 &entry/src/main/ets/pages/Index&
```

## cannot find module 'fileName', which is application Entry Point.

**Symptom**

Error reported when the application starts: cannot find module 'fileName', which is application Entry Point.

**Possible Causes**

The application did not upgrade its version number during the upgrade, or the application uses the [normalized](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile-app#section13181758123312) feature but was not restarted during the upgrade or update.

**Solution**

1. Use clean to delete the DevEco Studio cache and rebuild.

2. Check whether the versionCode in the crash file is consistent with the versionCode in module.json of the hap package.

   If they are inconsistent, the update failed because the application version number was downgraded. The application needs to update its version number.



3. Check whether the normalized feature is used but the application was not restarted.

   Check that the decompiled abc file is in the normalized ohmurl format. You can search for @normalized in the file:


4. Restart the application to ensure that the normalized feature takes effect.

**Reference**

[Disassembler tool](./tool-disassembler.md)

## cannot find record 'fileName', please check request path.

**Symptom**

Error reported at application runtime: cannot find record 'fileName', please check request path. This indicates that the specified module or file cannot be found, causing the application to run abnormally.

**Possible Causes**

1. The file uses dynamic import to load a module, but the [related configuration](./arkts-dynamic-import.md#dynamic-imports-with-variable-expressions) is not set in "buildOption" of build-profile.json5.

2. The file path is configured incorrectly, so the corresponding file cannot be found in the hap package.

**Solution**

1. Check whether the configuration of the dynamically loaded file is correct.

   Check it according to [dynamic loading syntax](./arkts-dynamic-import.md#key-points-in-dynamic-import-implementation).

2. Check whether the file path matches the compilation output.

      To reproduce the issue in a local project, search for the reported file path in entry/build/default/cache/default/default@CompileArkTS/esmodule/release/filesInfo.txt (using the release project as an example). There are two possible search results:

   Case 1: The complete file name cannot be found, but a similar name can be found.


      Solution: The complete name appears between the first and second semicolons on each line. The file name in the error message and the file name in the build output must be modified to be consistent.

   Case 2: The file cannot be found in filesInfo.txt, and no corresponding output file is generated in the build output area.


      Solution: Every file packaged into an abc is generated in the build output, such as entry packages and har packages. If developers cannot find the file at the corresponding path, check whether it is a dynamically loaded file.

**Reference Links**

[Dynamic Loading](./arkts-dynamic-import.md)