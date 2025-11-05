# @ohos.file.statvfs (文件系统空间统计)

该模块提供文件系统相关存储信息的功能：向应用程序提供获取文件系统总字节数、空闲字节数的JS接口。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { statfs } from '@kit.CoreFileKit';
```

## statfs.getFreeSize

ArkTS-Dyn: getFreeSize(path:string): Promise&lt;number&gt;

ArkTS-Sta: getFreeSize(path:string): Promise&lt;long&gt;

异步方法获取指定文件系统空闲字节数，以Promise形式返回结果。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名 | 类型   | 必填 | 说明                         |
  | ------ | ------ | ---- | ---------------------------- |
  | path   | string | 是   | 需要查询的文件系统的文件路径。 |

**返回值：**

  | 类型                  | 说明           |
  | --------------------- | -------------- |
  | ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;long&gt; | Promise对象，返回空闲字节数。 |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getFreeSize(path).then((number: number) => {
    console.info("getFreeSize succeed, Size: " + number);
  }).catch((err: BusinessError) => {
    console.error("getFreeSize failed with error message: " + err.message + ", error code: " + err.code);
  });
  ```
ArkTS-Sta示例：
<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getFreeSize(path).then((number: long) => {
    console.info(`Succeeded in getFreeSize, Size: ${number}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to getFreeSize. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## statfs.getFreeSize

ArkTS-Dyn: getFreeSize(path:string, callback:AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getFreeSize(path:string, callback:AsyncCallback&lt;long&gt;): void

异步方法获取指定文件系统空闲字节数，使用callback形式返回结果。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名   | 类型                        | 必填 | 说明                         |
  | -------- | --------------------------- | ---- | ---------------------------- |
  | path     | string                      | 是   | 需要查询的文件系统的文件路径。 |
  | callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;long&gt; | 是   | 异步获取空闲字节数之后的回调。 |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getFreeSize(path, (err: BusinessError, number: number) => {
    if (err) {
      console.error("getFreeSize failed with error message: " + err.message + ", error code: " + err.code);
    } else {
      console.info("getFreeSize succeed, Size: " + number);
    }
  });
  ```
ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getFreeSize(path, (err: BusinessError | null, number: long | undefined) => {
  if (err) {
    console.error(`Failed to getFreeSize. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getFreeSize, Size: ${number}`);
  }
});
```

## statfs.getFreeSizeSync<sup>10+</sup>

ArkTS-Dyn: getFreeSizeSync(path:string): number

ArkTS-Sta: getFreeSizeSync(path:string): long

以同步方法获取指定文件系统空闲字节数。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名 | 类型   | 必填 | 说明                         |
  | ------ | ------ | ---- | ---------------------------- |
  | path   | string | 是   | 需要查询的文件系统的文件路径。 |

**返回值：**

  | 类型                  | 说明           |
  | --------------------- | -------------- |
  | ArkTS-Dyn: number<br>ArkTS-Sta: long | 返回空闲字节数。 |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  let number = statfs.getFreeSizeSync(path);
  console.info("getFreeSizeSync succeed, Size: " + number);
  ```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
let num = statfs.getFreeSizeSync(path);
console.info(`Succeeded in getFreeSizeSync, Size: ${num}`);
```

## statfs.getTotalSize

ArkTS-Dyn: getTotalSize(path: string): Promise&lt;number&gt;

ArkTS-Sta: getTotalSize(path: string): Promise&lt;long&gt;

异步方法获取指定文件系统总字节数，以Promise形式返回结果。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名 | 类型   | 必填 | 说明                         |
  | ---- | ------ | ---- | ---------------------------- |
  | path | string | 是   | 需要查询的文件系统的文件路径。 |

**返回值：**

  | 类型                  | 说明         |
  | --------------------- | ------------ |
  | ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;long&gt; | Promise对象，返回总字节数。 |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getTotalSize(path).then((number: number) => {
    console.info("getTotalSize succeed, Size: " + number);
  }).catch((err: BusinessError) => {
    console.error("getTotalSize failed with error message: " + err.message + ", error code: " + err.code);
  });
  ```
ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalSize(path).then((number: long) => {
  console.info("getTotalSize succeed, Size: " + number);
  console.info(`Succeeded in getTotalSize, Size: ${number}`);
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to getTotalSize. Code: ${err.code}, message: ${err.message}`);
});
```

## statfs.getTotalSize

ArkTS-Dyn: getTotalSize(path: string, callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getTotalSize(path: string, callback: AsyncCallback&lt;long&gt;): void

异步方法获取指定文件系统总字节数，使用callback形式返回结果。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名   | 类型                        | 必填 | 说明                         |
  | -------- | --------------------------- | ---- | ---------------------------- |
  | path     | string                      | 是   | 需要查询的文件系统的文件路径。 |
  | callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;long&gt; | 是   | 异步获取总字节数之后的回调。   |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getTotalSize(path, (err: BusinessError, number: number) => {
    if (err) {
      console.error("getTotalSize failed with error message: " + err.message + ", error code: " + err.code);
    } else {
      console.info("getTotalSize succeed, Size: " + number);
    }
  });
  ```
ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
statfs.getTotalSize(path, (err: BusinessError | null, number: long | undefined) => {
  if (err) {
    console.error(`Failed to getTotalSize. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getTotalSize, Size: ${number}`);
  }
});
```

## statfs.getTotalSizeSync<sup>10+</sup>

ArkTS-Dyn: getTotalSizeSync(path: string): number

ArkTS-Sta: getTotalSizeSync(path: string): long

以同步方法获取指定文件系统总字节数。

**系统能力**：SystemCapability.FileManagement.File.FileIO

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

  | 参数名 | 类型   | 必填 | 说明                         |
  | ---- | ------ | ---- | ---------------------------- |
  | path | string | 是   | 需要查询的文件系统的文件路径。 |

**返回值：**

  | 类型                  | 说明         |
  | --------------------- | ------------ |
  | ArkTS-Dyn: number<br>ArkTS-Sta: long | 返回总字节数。 |

**错误码：**

接口抛出错误码的详细介绍请参见[基础文件IO错误码](errorcode-filemanagement.md#基础文件io错误码)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：
<!--code_no_check-->
  ```ts
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  let number = statfs.getTotalSizeSync(path);
  console.info("getTotalSizeSync succeed, Size: " + number);
  ```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.filesDir;
let num = statfs.getTotalSizeSync(path);
console.info(`Succeeded in getTotalSizeSync, Size: ${num}`);
```
