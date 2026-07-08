# ArkTS语言模块化加载异常常见问题

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @shilei123-->
<!--Designer: @shilei123;@yao_dashuai-->
<!--Tester: @kir175; @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->


##  ArkTS 应用运行时出现模块化加载相关的异常报错提示，可能的报错原因以及解决方法
### "Cannot find dynamic-import module 'xxxx'"

报错表示当前加载的模块未被编译到当前应用包内

**报错原因:**

通过动态加载传入表达式作为入参时，模块路径参数书写有误。
``` typescript
  import(module).then(m=>{m.foo();}).catch((e: Error)=>{console.error(e.message)});
```

**定位方法:**

打印待加载模块的路径信息，评估模块路径是否计算有误。

### "Cannot find module 'xxxx' , which is application Entry Point" 
报错表示拉起应用abc时，应用入口文件查找失败

**报错原因:**

在应用拉起时，查找应用入口文件模块失败。

**定位方法:**

(1) 打开应用工程级编译构建文件: entry > src/main/module.json5

([OpenHarmony工程管理介绍](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V3/ohos-project-overview-0000001218440650-V3))

module.json5部分参数示例如下:
``` json5
{
  "module": {
    "name": "entry",
    "type": "entry",
    ...
    "abilities": [
      {
        "name": "EntryAbility", // 模块名称
        "srcEntry": "./ets/entryability/EntryAbility.ts",  // 标明src目录相对工程根目录的相对路径
        "description": "$string:EntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:EntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background",
        "exported": true,
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "action.system.home"
            ]
          }
        ]
      }
    ]
  }
}
```
(2) 其中，"abilities":"srcEntry" 参数标记了该应用拉起的入口文件。如报错入口文件加载失败，请检查module.json5内的"srcEntry"参数是否书写正确。

### "No export named 'xxxx' which exported by 'xxxx'"
报错表示加载应用hap或har包内so时，该模块内未查找到特定对象

**报错原因:**

ets在模块化静态编译阶段，会预解析模块间的依赖关系。ets文件内的导入变量名书写错误时，ide编译器与应用编译阶段均会报错提示。但目前对于应用内native C++模块的依赖关系检测会在运行阶段。

**定位方法:**

检查应用内so是否存在报错提示的导出变量，并与加载应用内so的导入变量进行比较。如果不一致，则进行适配修改。


## ArkTS/Ts/Js加载so失败，表现行为是怎么样的

加载so失败后，不显式抛出加载失败的js异常。开发者可以通过导出对象是否为undefined判断so的加载状态；错误原因通过`NativeModuleErrorInfo`字段输出到JS Crash faultlog和hilog。

**so加载失败的错误信息（NativeModuleErrorInfo）说明**

`loadNativeModule`、`import()`等接口加载.so失败时，系统会将精确的错误原因写入`NativeModuleErrorInfo`字段，并通过JS Crash faultlog和hilog输出。开发者可在faultlog或`hilog | grep NativeModuleManager`中搜索下列错误信息字符串进行定位。

**错误场景与错误信息对照表**

| 错误信息（NativeModuleErrorInfo） | 触发场景 | 可能原因 | 处理步骤 |
| -------- | -------- | -------- | -------- |
| `moduleName is nullptr` | 调用加载接口时`moduleName`入参为空 | 代码传入了空字符串或未初始化变量 | 检查`loadNativeModule(moduleName)`的入参，确保`moduleName`非空 |
| `relativePath is nullptr` | `relativePath`参数为空 | 未传入相对路径或传入了null | 检查`relativePath`参数取值 |
| `invalid relativePath` | `relativePath`包含`..`路径穿越符 | 相对路径试图跳出允许的目录范围 | 修正`relativePath`，去掉`..`，仅使用模块内相对路径 |
| `module {moduleName} is in blocklist` | 目标模块在系统黑名单中 | 该.so被系统安全策略禁止加载 | 联系系统团队确认黑名单策略；普通应用不应依赖被列入黑名单的模块 |
| `module not found` | 模块文件未找到 | 模块未打包进HAP/HSP，或`oh-package.json5`的dependencies配置缺失 | 检查`oh-package.json5`的dependencies是否声明该模块；检查`build-profile.json5`的`runtimeOnly`配置；确认HAP包内存在对应.so文件 |
| `app lib path not registered in namespace '{path}'` | 应用lib路径未在namespace中注册 | 应用沙箱内namespace配置缺失或路径错误 | 检查应用`module.json5`与打包配置；确认应用的lib路径在namespace允许列表中 |
| `dlopen failed: {dlerror}` | `dlopen`系统调用失败 | .so文件损坏、架构不匹配（例如arm64的.so运行在arm32设备）、依赖的其他.so缺失、符号找不到 | 根据`{dlerror}`具体提示定位：`symbol not found`（缺符号）、`cannot open shared object file`（依赖缺失）、`wrong ELF class`（架构不匹配）、`file too short`（文件损坏） |
| `internal error: module create failed` | NativeModule对象创建失败 | 内存不足（OOM）、内部符号解析失败、NativeModule初始化异常 | 查看hilog中相关`NativeModuleManager`日志定位初始化失败原因；排查设备内存状态 |

>**说明**
>
>  - 成功加载.so时不会写入`NativeModuleErrorInfo`，对正常加载流程无影响。
>  - `NativeModuleErrorInfo`仅在faultlog和内部日志中可见，不会通过JS异常直接抛出；开发者仍需按上述"加载失败具体表现"通过`undefined`判断等方式检测加载状态。
>  - 如需开启更详细的模块加载日志，可执行`hdc shell param set persist.ark.properties 0x80105C`并重启设备。

**加载失败具体表现**  

| 加载类型 | ts/js模块 | 系统库so或应用so（JS层面） |
| -------- | -------- | -------- |
| 静态加载 | 虚拟机自动抛出异常，进程退出 | 无异常抛出，加载到的对象为undefined |
| 动态加载 | 不主动抛出异常，走到reject分支，开发者可以调用catch方法来捕获这个错误 | 不主动抛出异常，依然进入resolve分支，开发者可以在resolve分支中检查模块导出变量是否为undefined |
 
**示例1：系统库so或应用so静态加载失败**

``` ts
import testNapi from 'libentry.so'

if (testNapi == undefined) {
  console.error('load libentry.so failed.');
}
```

执行结果
``` ts
load libentry.so failed.
```

**示例2：系统库so或应用so动态加载失败**

``` ts
import('libentry.so')
  .then(m => {
    if (typeof m.default === 'undefined') {
      console.warn(`load libentry.so failed.`);
    } else {
      console.info('load libentry.so success:', m);
    }
    return m;
  })
  .catch((e: Error) => {
    console.error('load libentry.so error:', e);
  });
```

执行结果
``` ts
load libentry.so failed.
```

**参考文档**

- [Node-API常见问题](../napi/use-napi-faqs.md)
- [loadNativeModule](../reference/common/js-apis-common-load-native-module.md)
- [语言基础类库错误码10200301](../reference/apis-arkts/errorcode-utils.md)


## 模块间循环依赖导致运行时未初始化异常问题定位
### 循环依赖问题定位方法
报错xxx is not initialized不一定是循环依赖问题，需要打开开关进一步确认：
``` shell
打开option: hdc shell param set persist.ark.properties 0x2000105c
打开后必须重启机器：hdc shell reboot
如果需要关闭option: hdc shell param set persist.ark.properties 0x0000105c
关闭后必须重启机器：hdc shell reboot
```
开关打开后复现报错就是第一现场报错，解决即可。如果报错仍是xxx is not initialized, 就是文件存在循环依赖。

### 循环依赖原理
1. 模块加载顺序：

根据ECMA规范，模块的执行顺序是深度遍历加载。

假设应用存在加载链路A->B->C，那么ArkTs模块化会先执行C文件，再执行B文件，最后执行A文件，执行顺序为C->B->A。  
2. 循环依赖：

如果应用存在加载链路A->B->A，根据深度遍历执行顺序，执行流程会先标记A的状态为加载中，然后去加载B，标记B的状态为加载中，然后去加载A，由于A文件已经标记加载中，根据规范定义，识别到加载中模块会直接返回，就会先执行B文件。  
**为什么有的循环依赖没有影响，有的就会产生crash?**  
由上面的叙述可知，B文件虽然依赖A文件变量，但是B文件先执行，如果B文件导入的A文件变量没有在全局或者类静态中被使用，B文件将正常执行。如果B文件在全局或者实例化某个类等其他方法，导致文件执行时就会用到A的变量，就会产生xxx is not initialized的crash，即循环依赖导致变量未被初始化。

示例：
``` typescript
// A.ets
import { Animal } from './B'
export let a = "this is A";
export function A() {
  return new Animal;
}

// ---------------------

// B.ets
import { a } from './A'
export class Animal {
  static {
    console.info("this is in class");
    let str = a; // 报错信息：a is not initialized
  }
}
```
**正例**

``` typescript
// B.ets
import { a } from './A'
export class Animal {
  static {
    console.info("this is in class");
  }
  str = a;  // 修改点
}
```

### 循环依赖的解决方法：
[安全规则@security/no-cycle](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V5/ide_no-cycle-V5)


##  ArkTS 符号未初始化报错场景示例

ArkTS语言规范是基于ECMAScript规范的子集，根据语言规范，当访问一个还未完成初始化的符号时，运行时会抛出异常，为便于开发者定位解决源码问题，提供以下常见报错场景示例用于参考。

### const/let声明前访问

``` typescript
console.info(a); // 报错信息：Variable 'a' is used before being assigned.
console.info(b); // 报错信息：Variable 'b' is used before being assigned.

let a = '1';
const b = '2';
```
**正例**

``` typescript
let a = '1';
const b = '2';

console.info(a);
console.info(b);
```


### class声明前实例化

``` typescript
let a = new A(); // 报错信息：Class 'A' used before its declaration.

class A {}
```

**正例**

``` typescript
class A {}

let a = new A();
```

### class声明前访问其静态属性

``` typescript
let a = A.a; // 报错信息：Class 'A' used before its declaration.

class A {
  static a = 1;
}
```

**正例**

``` typescript
class A {
  static a = 1;
}

let a = A.a;
```

### 在函数中访问未提前声明的let和const变量

``` typescript
foo(); // 报错信息：Error message:a is not initialized

let a = 1;
const b = 2;

function foo() {
  let v = a + b;
}
```

**正例**

``` typescript
let a = 1;
const b = 2;

function foo() {
  let v = a + b;
}

foo();
```

### 在函数中访问未提前声明的类的静态属性

``` typescript
foo(); // 报错信息：Error message:A is not initialized

class A {
  static a = 1;
}

function foo() {
  let v = A.a;
  let w = new A();
}
```

**正例**

``` typescript
class A {
  static a = 1;
}

function foo() {
  let v = A.a;
  let w = new A();
}

foo();
```

### 模块间循环依赖 - const/let

``` typescript
// module1.ets
import { a, b } from './module2'

export let i = 1;
export let m = a;
export const j = 2;
export const n = b;

// ---------------------

// module2.ets
import { i, j } from './module1'

export let a = i; // 报错信息：Error message:i is not initialized
export const b = j; // 报错信息：Error message:j is not initialized
```

**解决方法**

详见[循环依赖的解决方法](#循环依赖的解决方法)


### 模块间循环依赖 - class

``` typescript
// class1.ets
import { b } from './class2'

export class A {
  static a = b;
}

// ---------------------

// class2.ets
import { A } from './class1'
export let b = 1;

const i = A.a; // 报错信息：Error message:A is not initialized
const j = new A(); // 报错信息：Error message:A is not initialized
```

**解决方法**

详见[循环依赖的解决方法](#循环依赖的解决方法)