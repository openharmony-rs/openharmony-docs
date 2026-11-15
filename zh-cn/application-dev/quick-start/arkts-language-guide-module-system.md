---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS基于ES模块的import/export语法体系，涵盖静态导入、动态导入、模块懒加载、模块组织、顶层语句及.d.ets声明文件。"
keywords: [ArkTS, 模块系统, import, export, 静态导入, 动态导入, 声明文件, ES模块]
doctype: guide
status: active
---

# 模块系统
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

模块系统用于把代码拆分为边界清晰、可复用、可维护的文件。本章介绍模块的基础概念、导出与导入语法、动态导入与懒加载、模块路径与模块组织方式、顶层语句的执行时机，以及`.d.ets`声明文件。

## 模块基础

模块是组织代码的基本单位，通过导入导出实现复用。

### 模块的定义

在ArkTS中，一个文件即一个模块。模块中的变量、函数、类、接口默认只在当前文件可见，只有通过`export`导出的声明才能被其他模块导入。

<!-- @[module_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/User.ets) -->

``` TypeScript
// User.ets
export interface User {
  id: number;
  name: string;
}

export function createUser(id: number, name: string): User {
  return {
    id: id,
    name: name
  };
}

export class UserService {
  private users: User[] = [];

  add(user: User): void {
    this.users.push(user);
  }

  getAll(): User[] {
    return this.users;
  }
}
```

## export导出

通过`export`可将模块内的声明标记为公开API，供其他模块按需导入复用，支持命名导出和默认导出两种形式。

### 声明时导出

可以在声明变量、常量、函数、类、接口或类型别名时直接导出。

<!-- @[named_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
export const MAX_RETRY_COUNT: number = 3;

export let currentUserName: string = '';

export interface RequestConfig {
  url: string;
  timeout: number;
}

export type RequestStatus = 'idle' | 'loading' | 'success' | 'failed';

export function buildUrl(baseUrl: string, path: string): string {
  return baseUrl + path;
}

export class RequestTracker {
  private status: RequestStatus = 'idle';

  setStatus(status: RequestStatus): void {
    this.status = status;
  }

  getStatus(): RequestStatus {
    return this.status;
  }
}
```

### 统一导出

也可以先声明，再在文件末尾统一导出。统一导出适合让模块的公开API集中可见。

<!-- @[export_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
const DEFAULT_TIMEOUT: number = 5000;

interface ApiConfig {
  host: string;
  timeout: number;
}

function createApiConfig(host: string): ApiConfig {
  return {
    host: host,
    timeout: DEFAULT_TIMEOUT
  };
}

export { ApiConfig, DEFAULT_TIMEOUT, createApiConfig };
```

### 重命名导出

使用`export { name as newName }`语法在导出时重命名绑定，避免命名冲突或提升API可读性。

<!-- @[export_rename](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
class InternalUserService {
  getName(): string {
    return 'UserService';
  }
}

export { InternalUserService as RenamedUserService };
```

### 默认导出

默认导出使用`export default`导出主要功能，导入时可使用任意名称。

<!-- @[default_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Logger.ets) -->

``` TypeScript
// Logger.ets
export default class Logger {
  info(message: string): void {
    console.info(`${message}`);
  }
}
```

在另一个文件中，可以通过默认导入使用该类。

<!-- @[default_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/DefaultImport.ets) -->

``` TypeScript
import Logger from '../common/Logger';

let logger: Logger = new Logger();
logger.info('module loaded');
```
大型项目中，公共API通常优先使用命名导出，因为命名导出在代码检索、重构维护和接口约束方面具有明显优势。

### 重新导出

重新导出常用于模块入口文件，把同一领域下的多个文件聚合成一个稳定入口。

<!-- @[submodule_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
export interface User {
  id: number;
  name: string;
}
```

在另一个源文件中定义服务类，对外提供业务方法。

<!-- @[submodule_export_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Service.ets) -->

``` TypeScript
import { User, Product } from './Types';

export class UserService {
  findById(id: number): User | null {
    if (id <= 0) {
      return null;
    }
    return {
      id: id,
      name: 'Alice'
    };
  }
}
```

随后通过桶文件将这些分散的导出聚合为统一入口，例如在`pages`目录下创建桶文件`ModuleSystem.ets`：

<!-- @[barrel_file_reexport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
export { User } from '../common/Types';
export { UserService } from '../common/Service';
```

使用方只需从桶文件导入，无需关心各成员的来源文件。需要注意的是，从桶文件导入会解析并执行整条依赖链上的模块，性能敏感场景的优化建议见[import路径展开](../arkts-utils/arkts-module-side-effects.md#通过import路径展开优化性能)。

<!-- @[barrel_file_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/BarrelFileImport.ets) -->

``` TypeScript
import { User, UserService } from './ModuleSystem';

let service: UserService = new UserService();
let user: User | null = service.findById(1);
console.info(`${user ? user.name : 'not found'}`);
```

## 静态导入

通过`import`引入其他模块导出的绑定，在当前文件中使用其类型、函数或类，支持命名导入和整体导入。

### 命名导入

使用`import { name } from 'path'`按名称导入模块的命名导出，大括号内可列出多个绑定。

<!-- @[named_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/NamedImport.ets) -->

``` TypeScript
import { UserService } from '../common/User';

let service: UserService = new UserService();
```

### 重命名导入

当导入名称与当前文件已有名称冲突，或需要提高可读性时，建议重命名。

<!-- @[import_rename](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ImportRename.ets) -->

``` TypeScript
import { UserService as AccountUserService } from '../common/User';

let service: AccountUserService = new AccountUserService();
```

### 默认导入

使用`import Name from 'path'`导入模块的默认导出，名称无需与导出时一致。

<!-- @[default_import_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/DefaultImport.ets) -->

``` TypeScript
import Logger from '../common/Logger';

let logger: Logger = new Logger();
```

### 默认导入与命名导入组合

使用`import defaultName, { namedName } from 'path'`在同一条语句中同时导入默认导出和命名导出。

<!-- @[mixed_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Report.ets) -->

``` TypeScript
// Report.ets
export interface ReportOptions {
  title: string;
}

export default class ReportBuilder {
  build(options: ReportOptions): string {
    return options.title;
  }
}
```

在消费端可以同时导入默认导出和命名导出。

<!-- @[mixed_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/MixedImport.ets) -->

``` TypeScript
import ReportBuilder, { ReportOptions } from '../common/Report';

let options: ReportOptions = {
  title: 'Daily'
};
let builder: ReportBuilder = new ReportBuilder();
let title: string = builder.build(options);
console.info(`${title}`);
```

### 命名空间导入

使用`import * as name from 'path'`把目标模块的全部命名导出收拢到一个对象上，通过`name.成员名`访问。

<!-- @[export_multiple_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Math.ets) -->

``` TypeScript
// Math.ets
export function add(left: number, right: number): number {
  return left + right;
}

export function multiply(left: number, right: number): number {
  return left * right;
}
```

导入方通过统一的对象前缀访问全部成员。

<!-- @[namespace_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/NamespaceImport.ets) -->

``` TypeScript
import * as MathUtil from '../common/Math';

let sum: number = MathUtil.add(1, 2);
let product: number = MathUtil.multiply(3, 4);
console.info(`${sum}, ${product}`);
```

命名空间导入适合导出成员较多、且希望调用处保留来源前缀的工具模块；日常场景推荐命名导入，按需引入、依赖更清晰。

### 副作用导入

不带任何绑定的`import 'path'`只触发目标模块的加载执行，不引入它的任何导出，适用于模块在加载时自行完成初始化、注册等工作的场景。

<!-- @[side_effect_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Config.ets) -->

``` TypeScript
// Config.ets：顶层代码在模块被加载时执行
console.info('Config initialized');

export const APP_LABEL: string = 'DemoApp';
```

下面的语句不使用`Config`模块的任何导出，仅确保其顶层代码先于当前文件执行：

<!-- @[side_effect_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SideEffectImport.ets) -->

``` TypeScript
import '../common/Config';
```

模块加载可能引发的副作用及优化方式，见[模块加载副作用及优化](../arkts-utils/arkts-module-side-effects.md)。

<!--RP1--><!--RP1End-->

## 动态导入

使用`import()`在运行时按需加载模块，适用于按条件加载、延迟初始化等场景。

### 基本写法

动态导入用于按需加载模块。它返回`Promise`，因此通常与`async`/`await`搭配使用。

<!-- @[dynamic_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
async function loadFeatureLabel(): Promise<string> {
  let moduleObject = await import('../common/Feature');
  return moduleObject.getFeatureLabel();
}
```

被动态加载的模块照常导出成员。

<!-- @[dynamic_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Feature.ets) -->

``` TypeScript
export function getFeatureLabel(): string {
  return 'feature';
}
```

### 使用限制

动态导入的模块路径应保持可静态分析。涉及打包、分包、跨包加载或运行时权限时，需要遵循HarmonyOS工程和运行时约束。动态`import`还支持按需加载HSP/HAR/ohpm包等场景，适用场景与完整用法见[动态加载](../arkts-utils/arkts-dynamic-import.md)。

<!-- @[conditional_dynamic_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
async function loadByName(name: string): Promise<string> {
  if (name === 'profile') {
    let profileModule = await import('../common/ProfileFeature');
    return profileModule.getProfileLabel();
  }

  if (name === 'settings') {
    let settingsModule = await import('../common/SettingsFeature');
    return settingsModule.getSettingsLabel();
  }

  return 'unknown';
}
```

## 模块懒加载

在`import`语句中添加`lazy`关键字，可以把目标模块的执行推迟到导入的变量首次被使用时，从而缩短应用的冷启动时间。冷启动阶段只解析依赖、不执行模块源码；变量被访问时才同步触发模块执行。该特性从API version 12开始支持。

<!-- @[lazy_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/ModuleSystem.ts) -->

``` TypeScript
// main.ts
import lazy { a } from './mod1';  // 冷启动时不执行mod1.ts的顶层代码

export function loadOnDemand(): string {
  return a;  // a首次被使用时，才触发mod1.ts的加载与执行
}
```

<!-- @[lazy_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/mod1.ts) -->

``` TypeScript
// mod1.ts
export let a = 'mod1 executed';
```

与动态导入相比，懒加载保持静态导入写法、写在源码开头，触发加载时同步执行。完整语法规格、使用限制与错误示例，见[延迟加载（lazy import）](../arkts-utils/arkts-lazy-import.md)。

## 模块路径

模块路径指定导入导出的源文件位置，ArkTS支持相对路径（`./`或`../`开头）与ohpm包名两种形式。相对路径可省略文件扩展名；导入ohpm包中的模块时直接使用包名，如`import { describe } from '@ohos/hypium'`。

### 相对路径

相对路径适合表达当前模块附近的依赖关系。

<!-- @[relative_path_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/RelativePathImport.ets) -->

``` TypeScript
import { User } from '../common/User';
import { AppConfig } from '../config/appConfig';
import { UserRepository } from '../common/Repository';
```

## 模块组织

通过目录结构和桶文件（barrel file）管理多个模块的导出。

### 按领域组织

按领域组织模块将相关功能集中，提高代码的可维护性。

<!-- @[submodule_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
export interface User {
  id: number;
  name: string;
}
```

同一目录下的仓储类导入并使用上述类型。

<!-- @[submodule_repository](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Repository.ets) -->

``` TypeScript
import { User } from './Types';

export class UserRepository {
  private users: User[] = [];

  save(user: User): void {
    this.users.push(user);
  }

  list(): User[] {
    return this.users;
  }
}
```

再通过桶文件将各模块的公开API汇总对外暴露。

<!-- @[submodule_barrel_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SubmoduleBarrelFile.ets) -->

``` TypeScript
export { User } from '../common/Types';
export { UserRepository } from '../common/Repository';
```

### 避免循环依赖

循环依赖会让模块初始化顺序变复杂。出现相互导入时，优先把共同类型、常量或接口提取到独立模块。

<!-- @[shared_types_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
// Types.ets
export interface UserIdentity {
  id: number;
}
```

其他模块导入共享类型后即可使用，无需彼此直接依赖。

<!-- @[shared_types_usage_profile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SharedTypesUsage.ets) -->

``` TypeScript
import { UserIdentity } from '../common/Types';

export function getProfileName(identity: UserIdentity): string {
  return 'user-' + identity.id.toString();
}
```

同一共享类型可在多个模块中复用。

<!-- @[shared_types_usage_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SharedTypesUsage.ets) -->

``` TypeScript
export function canRead(identity: UserIdentity): boolean {
  return identity.id > 0;
}
```

## 顶层语句

模块最外层直接编写的代码称为顶层语句，不被函数、类或块级作用域包裹。顶层语句在模块首次被加载时按从上到下的顺序执行，常用于模块级别的初始化逻辑。被导入模块的顶层语句总是先于导入方执行。

<!-- @[top_level_statements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
// 模块顶层语句
let appConfig: string = 'production';
const MAX_RETRIES: number = 3;

function logConfig(): void {
  console.info(`Config: ${appConfig}, Retries: ${MAX_RETRIES}`);
}

// 顶层表达式
console.info('Module loaded');
logConfig();
```

上例中，`console.info('Module loaded')`与`logConfig()`在模块加载时立即执行，`logConfig()`能读取到先于它声明的`appConfig`和`MAX_RETRIES`。顶层语句应保持轻量，避免耗时初始化拖慢模块加载。模块执行的完整规则（加载顺序、单次执行语义、跨线程行为等）与加载流程，见[模块化运行简介](../arkts-utils/module-principle.md)。模块加载可能引发的副作用及优化方式，见[模块加载副作用及优化](../arkts-utils/arkts-module-side-effects.md)。

## 声明文件

声明文件是对模块对外能力的整体描述，只包含类型和接口的声明（如`interface`、函数签名等），不包含具体实现，供编译器进行类型检查。ArkTS使用`.d.ets`文件作为声明文件，作用与TypeScript中的`.d.ts`文件类似，常用于共享包对外提供的类型声明、NAPI原生模块导出对象的类型声明等场景。模块进行类型解析时，若目录下存在同名文件（后缀不同），默认优先加载`.d.ets`文件，其次加载`.d.ts`文件。

声明文件中使用`declare`关键字声明“在别处已实现”的实体：它告诉编译器该实体由实现文件或原生库提供，当前文件只描述其类型。例如`declare const`声明由其他模块或原生库定义的常量，`declare function`声明在别处实现的函数，`export declare`在声明的同时对外导出：

<!-- @[declaration_file_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Declaration.d.ets) -->

``` TypeScript
// common/Declaration.d.ets：声明文件只包含声明，不包含实现
declare const APP_VERSION: string;

declare function logConfig(): void;

declare class ConfigReader {
  read(key: string): string | undefined;
}

export declare function getConfig(name: string): string;
```
