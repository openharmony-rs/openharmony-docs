# 模块化运行简介 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @HelloCrease-->

ArkTS-Sta运行时采用基于ClassLinker+FileManager的模块加载体系，仅支持ES Module规范，运行时层面采用"编译时统一、运行时扁平"的设计理念。本文详细介绍ArkTS-Sta的模块化规范、模块类型、加载流程、类初始化机制、Native模块加载以及模块化常见问题的解决措施。

## ArkTS-Sta支持的模块化规范与模块类型

ArkTS-Sta仅支持ES Module规范，运行时可加载.abc字节码、.an AOT文件和Native .so模块。

### ArkTS-Sta的模块化规范

ArkTS-Sta运行时仅支持**ECMAScript模块规范**（ES Module），不支持CommonJS模块规范。

| 规范 | ArkTS-Sta支持情况 | 说明 |
| -------- | -------- | -------- |
| ES Module | 支持 | 通过export/import语法进行模块导出导入。 |
| CommonJS | 不支持 | ArkTS-Sta运行时无CommonJS模块加载机制。`require()`和`module.exports`不可用。 |

> **说明：**
>
> ArkTS-Sta不支持CommonJS模块，仅支持ES Module的`import/export`语法。如果需要在ArkTS-Sta中访问JS侧的CommonJS模块对象，需通过互操作层（Interop Layer）的JSRuntime代理机制间接访问。

### ArkTS-Sta支持的模块类型

ArkTS-Sta运行时在运行时层面仅处理**编译产物**，不区分源文件类型：

| 模块类型 | 运行时处理方式 | 说明 |
| -------- | -------- | -------- |
| .ets/.ts源文件 | 编译为.abc字节码文件后加载。 | 所有源文件类型在编译阶段由前端编译器（es2panda）统一编译为.abc字节码文件，运行时不区分源文件类型。 |
| .abc字节码文件 | 通过FileManager打开、ClassLinker加载。 | 运行时的主要加载单位，包含类定义、方法字节码、常量池等。 |
| .an AOT文件 | AOT启用时自动加载。 | 若启用了AOT编译，运行时在加载.abc时同时查找对应的.an文件以获得预编译的机器码。 |
| Native模块（.so） | 通过NativeLibraryProvider加载。 | 使用ANI机制加载，详见[Native模块加载](#native模块加载)章节。 |
| JSON文件 | 不支持作为模块导入。 | ArkTS-Sta不支持`import data from './data.json'`语法。JSON数据通过`JSON.parse()`和`JsonElement`序列化/反序列化API处理。 |

> **说明：**
>
> ArkTS-Sta运行时采用"编译时统一、运行时扁平"的设计理念。所有.ets/.ts源文件在编译阶段被统一处理为.abc字节码文件，运行时仅看到.abc文件，无需区分原始源文件的语言类型。这与ArkTS-Dyn运行时在运行时层面区分不同语言类型的模块形成关键差异。
>
> 模块的import路径解析（如将`./components/entry`解析为具体的文件路径）全部由前端编译器在编译阶段完成，运行时不负责import路径解析，仅根据类型描述符（如`Lstd/core/Object;`）在已加载的.abc文件中查找和加载类。

## 模块化概述

ArkTS-Sta的模块化基于ES Module规范，支持模块声明、命名空间合并、导入导出指令和类型注解约束。

### ArkTS-Sta的模块声明

程序由**模块**构成，模块是顶级命名空间的特定形式。每个模块创建自己的作用域，未导出的声明仅在模块内可见。

模块可选组成部分：
1. 模块头（定义模块名）。
2. Import指令。
3. 顶级声明。
4. 顶级语句。
5. Re-export指令。

### 命名空间

命名空间引入带可区分名称的实体容器，可包含嵌套命名空间：

- 命名空间初始化器仅在导出成员被使用时执行。
- 同名命名空间在同一模块内合并导出声明。
- `namespace A.B` 是 `namespace A { export namespace B }` 的简写。

### Import指令

三种绑定形式：

| 加载类型 | 写法 | 说明 |
| -------- | -------- | -------- |
| 全量导入 | `import * as M from "path"` | 代码可读性高。 |
| 默认导入 | `import X from "path"` | 导入default导出。 |
| 选择性导入 | `import {sin, PI} from "path"` | 按名导入，可别名。 |

Import路径：
- 相对路径：`./components/entry`, `../constants/http`。
- 非相对路径：依赖编译环境配置（baseUrl, paths映射）。

### Export指令

- `export`修饰符使声明在其他模块可通过import访问。
- **导出约束**：所有导出实体类型必须显式标注；导出声明不得引用未导出实体。
- **default导出**：每个模块仅允许一个default导出。
- **Re-export**：`export * from "path"` 或 `export {X as Y} from "path"`


所有导出实体必须显式标注类型，否则会产生编译错误：

- 导出变量/常量无显式类型。
- 导出函数无显式返回类型。
- 导出类public/protected字段无显式类型。
- 导出声明引用未导出实体。

## 模块化运行加载流程

ArkTS-Sta采用ClassLinker+FileManager加载模型，基于扁平Context体系和深度优先类初始化顺序运行模块。

### 加载模型与ArkTS-Dyn的差异

ArkTS-Sta运行时的模块加载基于**ClassLinker+FileManager**体系，与ArkTS-Dyn基于ECMAScript模块规范的加载模型有本质差异：

| 差异点 | ArkTS-Sta | ArkTS-Dyn |
| -------- | -------- | -------- |
| 加载引擎 | ClassLinker + EtsClassLinkerExtension | ECMAScript Module Loader |
| 加载单位 | Class（类型定义） | Module（文件模块） |
| 上下文模型 | BootstrapContext + AppContexts（扁平） | 模块命名空间对象 |
| 命名空间表示 | 降级为Class结构 + ets.annotation.Module注解 | 模块命名空间Exotic Object |
| 初始化 | \<cctor\>静态方法执行 | 模块顶层代码执行 |

### Context体系

ArkTS-Sta运行时使用扁平化类加载上下文，不采用Java式的parent-first层级委托模型：

- BootstrapContext：运行时核心类（ClassRoot定义的基础类型），优先加载。
- AppContext：每个.abc文件对应一个AppContext，存放该文件中定义的类。
- 类查找顺序：先在当前Context查找，再在BootstrapContext查找。

### 命名空间在二进制文件中的表示

命名空间降级为`Class`结构：

| 命名空间元素 | Class结构表示 |
| -------- | -------- |
| 模块本身 | 标记为abstract + `ets.annotation.Module`注解的Class |
| 变量/常量 | Class的字段 |
| 函数/访问器 | Class的方法 |
| 初始化器 | Class的`<cctor>`静态方法 |

示例：

```typescript
// 源码
namespace MathUtils {
  export const PI: double = 3.14159
  export function sin(x: double): double { ... }
}
```

编译后在.abc中生成类似：

```ts
Class: LMathUtils;
  access_flags: ACC_ABSTRACT | ACC_STATIC
  annotation: ets.annotation.Module
  fields:
    PI: double (static)
  methods:
    sin: <ctor>.double(double) (static)
    <cctor>: void() (static, 初始化器)
```

### 模块初始化执行顺序

与ArkTS-Dyn运行时采用全局后序遍历执行模块不同，ArkTS-Sta运行时采用**按需深度优先**的类初始化策略：

- 类仅在首次被访问时触发初始化（加载其`<cctor>`静态初始化块）。
- 初始化顺序遵循继承依赖：先初始化super类，再初始化接口，最后执行当前类的`<cctor>`。
- 不存在全局模块执行顺序——每个类按需初始化，哪个类先被访问就先初始化。

例如，如果类A的`<cctor>`引用了类B，则类B的`<cctor>`会在类A的`<cctor>`执行过程中被触发，确保B先完成初始化。

> **说明：**
>
> ArkTS-Dyn运行时在加载模块图时，会按后序遍历顺序统一执行所有模块的顶层代码。而ArkTS-Sta运行时没有全局模块执行顺序，类的`<cctor>`初始化是按需触发的。这意味着ArkTS-Sta中模块的初始化时机取决于类首次被访问的时间点，而非模块图的拓扑排序。

### 入口文件与入口点

ArkTS-Sta运行时的入口概念与ArkTS-Dyn不同：

- **入口点**：以`ClassName.methodName`格式指定（通常为`ETSGLOBAL.main`）。运行时从应用.abc文件中解析入口点，找到对应类和方法并执行。
- **ETSGLOBAL**：每个.abc文件中的顶级声明（包括顶级函数、顶级变量、模块初始化逻辑）被编译为`ETSGLOBAL`类的成员。`ETSGLOBAL`类的`<cctor>`方法包含了模块的静态初始化逻辑，`ETSGLOBAL.main`是应用的启动入口方法。

入口文件执行流程：
1. 运行时加载应用.abc文件，创建AppContext。
2. 解析入口点（如`ETSGLOBAL.main`），找到对应类和方法。
3. 初始化入口类（执行`ETSGLOBAL`的`<cctor>`，触发依赖类的按需初始化）。
4. 调用入口方法（`ETSGLOBAL.main`），应用开始执行。

> **说明：**
>
> ArkTS-Dyn中入口文件由框架API（如`windowStage.loadContent`）或路由跳转接口指定，入参文件作为入口文件执行。而ArkTS-Sta的入口点是编译时确定的`ClassName.methodName`格式，由运行时启动时直接解析和执行。

### 模块加载的线程语义

ArkTS-Sta运行时的模块加载是**进程级共享**的，与ArkTS-Dyn的线程级隔离不同：

- **类加载**：ClassLinkerContext中的类在进程内只加载一次，所有线程共享同一Class实例。类查找在共享的`loadedClasses_`哈希表中完成。
- **类初始化**：类的初始化状态（INITIALIZING/INITIALIZED/ERRONEOUS）是进程级共享的。多个线程同时触发同一类初始化时，通过锁机制保证只有一个线程执行`<cctor>`，其他线程等待。
- **模块对象**：与ArkTS-Dyn中"每个线程生成新的模块对象"不同，ArkTS-Sta中类和模块命名空间对象在进程内唯一。

> **说明：**
>
> ArkTS-Dyn运行时中"普通模块在同一线程内只加载一次，而在不同线程中会加载多次"。ArkTS-Sta运行时中类在进程内只加载一次，不区分线程。如果需要在进程内共享模块状态，ArkTS-Sta天然支持——因为类的静态字段本身就是进程级共享的。但ArkTS-Sta目前没有类似ArkTS-Dyn的SharedModule/SendableModule机制来支持跨Worker线程的安全共享对象。

### 模块加载方式

ArkTS-Sta运行时支持的模块加载方式与ArkTS-Dyn有显著差异：

| 加载方式 | ArkTS-Sta支持情况 | 说明 |
| -------- | -------- | -------- |
| 静态加载（import） | 支持 | 编译时解析、运行时按需初始化。 |
| 动态加载（import()） | 不支持 | ArkTS-Sta不支持`import()`动态导入语法。 |
| 延迟加载（lazy import） | 不支持 | ArkTS-Sta不支持延迟导入语法。 |
| initModule() | 支持 | 标准库函数，确保模块可用并完成初始化。 |
| AbcRuntimeLinker.addAbcFiles() | 支持 | 运行时API，向ClassLinker动态添加新的.abc文件。 |

> **说明：**
>
> ArkTS-Dyn运行时支持动态加载（`import()`）、延迟加载（lazy import）等多种灵活的模块加载方式。ArkTS-Sta运行时由于基于静态类型系统，不支持运行时的动态模块加载语法。如果需要在运行时动态添加模块，可通过`AbcRuntimeLinker.addAbcFiles()`API将新的.abc文件注册到ClassLinker，之后即可通过类描述符查找和加载其中的类。这种方式适用于插件式应用的动态模块加载场景。

## 类初始化机制

ArkTS-Sta通过ClassInitializer执行静态初始化块，处理重入检测、错误传播和模块标准库初始化。

### ClassInitializer

类初始化器处理\<cctor\>（静态初始化块）的执行：

- **重入检测**：`initTid_`记录正在初始化的线程ID。
  - 同一线程递归初始化同一类是合法的（`initTid_`检测）。
  - 不同线程初始化同一类时，后到线程等待前线程完成。
- **初始化顺序**：先初始化super类，再初始化当前类的\<cctor\>。
- **错误传播**：初始化失败时标记为ERRONEOUS，后续访问抛LinkerError。

### initModule标准库函数

`initModule("path")` 标准库函数确保模块可用并完成初始化：

```typescript
// 确保模块可用并完成初始化
initModule("./components/entry")
```

Import路径查找：文件夹先查 `index.ets`，再查 `index.ts`。

## Native模块加载

ArkTS-Sta运行时通过ANI（Ark Native Interface）机制加载Native模块（.so文件），与ArkTS-Dyn通过Node-API机制加载不同。

### 加载流程

1. 运行时通过NativeLibraryProvider使用`dlopen`加载.so文件。
2. 在.so文件中查找`ANI_Constructor`符号并调用，完成ANI接口的版本协商和初始化。
3. .so文件中导出的Native方法被注册为Class的方法，与普通方法统一管理。

### ANI方法调用类型

Native方法支持三种调用约定，根据性能和安全需求选择：

| 类型 | 说明 | GC安全性 | 适用场景 |
| -------- | -------- | -------- | -------- |
| GENERIC | 切换协程到Native模式，允许GC暂停。 | GC安全 | 通用Native方法，需要GC安全保证。 |
| FAST | 保持托管模式运行，不允许GC暂停。 | 不安全 | 高频调用的小方法，不涉及GC操作。 |
| CRITICAL | 保持托管模式运行，不允许GC暂停，直接传递参数。 | 不安全 | 极高频调用，方法必须为static。 |

> **注意：**
>
> FAST和CRITICAL类型的Native方法在执行期间GC不可暂停应用线程，因此Native代码中不能触发GC操作（如分配托管对象）。如果Native方法需要分配托管对象或可能触发GC，必须使用GENERIC类型。

### Native模块导入示例

```typescript
// libentry.so对应的类型声明文件
export const add: (a: number, b: number) => number;

// ArkTS-Sta代码中导入Native模块
import { add } from 'libentry.so';
add(2, 3);
```

> **说明：**
>
> 与ArkTS-Dyn使用Node-API（NAPI）机制加载Native模块不同，ArkTS-Sta使用ANI（Ark Native Interface）机制。ANI在类型系统层面与ArkTS-Sta的静态类型系统更紧密集成，支持更高效的方法调用约定（FAST/CRITICAL模式）。

## 模块化常见问题

以下是模块化开发中的常见问题及排查方向。

### 循环依赖导致类初始化失败

**问题现象**

应用运行时报错："Object is not initialized"或LinkerError，导致应用无法正常运行。

**可能原因**

模块之间存在循环依赖关系，导致类在访问时还未完成\<cctor\>初始化。

与ArkTS-Dyn的循环依赖不同，ArkTS-Sta的循环依赖发生在**类初始化阶段**而非模块执行阶段。如果类A的\<cctor\>触发类B初始化，类B的\<cctor\>又触发类A初始化，则形成循环依赖。

**解决措施**

1. 分析类初始化顺序，定位循环依赖的类关系。

2. 重构代码结构，消除循环依赖：
   - 将公共依赖提取到独立模块。
   - 调整类静态初始化块的执行顺序。
   - 使用延迟初始化替代\<cctor\>中的直接引用。

**代码示例**

```typescript
// 循环依赖示例
class A {
  static value: number = B.compute()  // A的<cctor>依赖B
}

class B {
  static compute(): number { return A.value + 1 }  // B的<cctor>依赖A
}
```

规避方案：使用延迟初始化。

```typescript
class A {
  static value: number = 0  // 先给默认值
  static init(): void { A.value = B.compute() }  // 延迟初始化
}

class B {
  static compute(): number { return 1 }  // 不依赖A的初始化值
}
```

### ERRONEOUS类访问

**问题现象**

运行时报LinkerError，提示类处于ERRONEOUS状态。

**可能原因**

类的\<cctor\>初始化过程中抛出了异常，导致类被标记为ERRONEOUS。后续任何对该类的访问都会抛LinkerError，不可恢复。

**解决措施**

1. 检查\<cctor\>中的代码逻辑，确保不会抛出异常。
2. 在\<cctor\>中使用try-catch捕获可能出现的异常并进行处理。
3. 避免在\<cctor\>中执行耗时操作或创建大量对象（可能触发GC导致额外风险）。

### 二进制兼容性导致的加载失败

**问题现象**

更新应用后运行时报LinkerUnresolvedClassError或LinkerMethodConflictError。

**可能原因**

独立编译的模块间因源码变更导致二进制不兼容。例如：
- 依赖的类被删除或重命名。
- public方法的签名发生了变化。
- 删除了public字段。

**解决措施**

1. 确保所有依赖模块使用相同版本编译。
2. 遵守二进制兼容性规则，避免不兼容的源码变更。
3. 使用运行时验证系统检测不兼容的二进制代码。

### 类初始化死锁

**问题现象**

应用启动时卡住，无法继续执行。

**可能原因**

两个线程同时初始化互相依赖的类：
- 线程1正在初始化类A，等待类B初始化完成。
- 线程2正在初始化类B，等待类A初始化完成。

**解决措施**

- 避免在\<cctor\>中启动新线程。
- 避免在\<cctor\>中创建TaskPool任务或EAWorker。
- 确保类的\<cctor\>初始化顺序是单向的，不形成循环依赖。
