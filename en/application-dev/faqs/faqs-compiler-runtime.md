# Compiler and Runtime


## What should I do if a crash occurs when I obtain a string in JSON format from rawfile, convert the string into an object, and call the instance method? (API version 9)

**Symptom**

"jscrash happened in xxxxxxxxx" is displayed, and the crash log contains "Error message: Unexpected Object in JSON".

**Solution**

The prototype of the object obtained by parsing the string in JSON format is object. The prototype chain does not contain the instance method. Therefore, the object cannot be called.

To solve this problem, use either of the following methods:

1. Add the prototype to the parsed object.

2. Change the instance method to a static method and call it through the class name.

## What should I do to prevent unexpected error behavior when **napi_call_function** is called again after a pending exception is captured in **napi_call_function**? (API version 10)

**Symptom**

When **napi_call_function** is called to invoke an ArkTs function, a pending exception is captured.

If security check is not performed upon a pending exception, an error will occur when **napi_call_function** is called next time and the error behavior is unpredictable.

**Solution**

If an error occurs when a native method using **napi_call_function** is called by ArkTS, throw jscrash. Then, try...catch on ArkTS will fail. If an exception occurs when **napi_call_function** is called, return a response in time.

## Are there any other exception scenarios besides the pending exception in **napi_call_function**? (API version 10)

**Solution**

Theoretically, an exception may occur when a Node-API interface is called. Therefore, in critical service processes, you must check the return results of interface calls to determine whether exceptions have occurred. The following is an example:
```cpp
napi_status status = napi_create_object(env, &object);
if (status != napi_ok) {
  napi_throw_error(env, ...);
  return;
}
```

## What should I do if cppcrash is logged with error "resolveBufferCallback get buffer failed" when multiple HSPs are loaded?

**Solution**

This problem is caused by a failure in parsing the HSP. Generally, a loading failure is caused when the HSP fails to be installed, the file to load does not exist, the application does not have the required permission, or the secure memory verification fails. Locate and resolve the problem based on the error information. Generally, the fault can be rectified by reinstalling the application.

| **Error Log**| **Solution**|
| -------- | -------- |
| realHapPath is empty | Failed to obtain information about the installation package. You are advised to reinstall the application.|
| transform real path error: ERROR, pathName: PATH | Failed to parse the path using **realpath()** function.** ERROR** indicates the error information, and **PATH** indicates the path of the HSP. You are advised to reinstall the application.|
| CreateFileMapper, mmap failed, errno ERROR. fileName: FILENAME | Failed to map the secure memory by using **mmap()** function. **ERROR** indicates the error information, and **FILENAME** indicates the file name. In this case, the system memory is insufficient or the file is not signed.|

## What is the maximum length of an array?

In the ECMAScript standard, the maximum array length is defined as 2^32 - 1. Attempting to set an array length beyond this value will result in a RangeError.

## What should I do if initialization errors occur at runtime due to inter-module circular dependency?

**Symptom**

Circular dependencies among modules may result in uninitialized variables in module dependencies during application runtime. The following provides an example. The dependent **page.ets** file is executed prior to the **index.ets** file. However, the execution of the **page.ets** file depends on the foo symbol exported by the **index.ets** file. At the moment, the **index.ets** file is not executed, and the foo variable is not initialized. As a result, an exception occurs at runtime.

```typescript
// index.ets
import { bar } from './page'

export function foo() {
    bar()
}

// page.ets
import { foo } from './index'

export function bar() {
    foo()
}
bar()

```

**Symptom**

A JS crash occurs at runtime. The error information "Error message: foo is not initialized" is recorded in the crash log.

**Solution**

You can use Code Linter in IDE to identify circular dependencies in the code and then refactor the code to eliminate the impact of circular dependencies. For details, see [Code Linter Check](https://developer.huawei.com/consumer/en/doc/harmonyos-guides-V5/ide-code-linter-V5). The procedure is as follows:

1. Create the **code-linter.json5** file in the root directory of the project and configure the file as follows:
    ```json5
    {
      "files": [ // The glob-pattern array is used to indicate the file range to which the configuration applies.
        "**/*.js",
        "**/*.ts",
        "**/*.ets"
      ],
      "rules": {
        "@security/no-cycle": "error" // Configure a circular dependency check rule.
      }
    }
    ```
2. In the project management window, right-click the root directory of the project and choose **Code Linter** > **Full Linter** to perform a full code check.
3. Based on the check result, reconstruct the code that involves circular dependencies.

## What should I do if compilation exception occurred with no specific error logs available, making it difficult to locate the root cause of the issue?
**Symptom**

The error message "Failed to execute es2abc." is displayed. However, no detailed error log is available, making it difficult to locate and analyze the fault.

**Symptom**

A large amount of deeply nested code is used, such as hundreds of layers of if-else statements, type conversions using **as**, and nested parentheses. During compilation, recursive calls exceed the stack capacity limit, leading to a crash of es2abc without any related error logs.

**Locating**

On Windows, you can open the Event Viewer, choose **Windows Logs** > **Application**, and look for the corresponding timestamp. If you find the crash log for es2abc.exe and the exception code is 0xc00000fd, it indicates that the compilation crashed due to a stack overflow.

On macOS, access Console, navigate to **Crash Reports**, find **es2abc**, and double-click it to view the crash log.

If the following information is displayed, the call stack repeatedly calls the same function. It indicates that excessive recursion has led to a stack overflow.

**Solution**

Check the code to identify any instances of extensive nested structures, like hundreds of layers of if-else statements, type conversions using **as**, and nested parentheses, and then proceed to break them down or enhance their efficiency.

**Example of Problematic Code**

Examples of deeply nested code are as follows:

```typescript
if (condition) {
    if (condition) {
        if (condition) {
            if (condition) {
                if (condition) {
                    if (condition) {
                        ...
                    }
                }
            }
        }
    }
}
```

```typescript
[
    [
        [
            [
                [
                    [
                        [
                            [
                                ...
                            ]
                        ]
                    ]
                ]
            ]
        ]
    ]
]
```

```typescript
!!!!!!!!!!
!!!!!!!!!!
...
!!!!!a
```

```typescript
var a = 1
a as Int as Int as Int as Int as Int ...
```
