---
kits: ["ArkTS Kit"]
description: "ArkTS ES module-based import/export syntax, covering static imports, dynamic imports, lazy loading, module organization, top-level statements, and .d.ets declaration files."
keywords: [ArkTS, module system, import, export, static import, dynamic import, declaration files, ES modules]
doctype: guide
status: active
---

# Module System
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8923bda514baa1452b967ea964ea779c7417bd8e translatedAt=2026-11-12T12:34:02.429Z pushedAt=2026-10-30T06:21:33.935Z nl=1 -->

The module system divides code into reusable, maintainable files with clear boundaries. This topic describes module basics, export and import syntax, dynamic imports and lazy loading, module paths and organization, top-level statement execution, and `.d.ets` declaration files.

## Module Basics

A module is the basic unit for organizing code, and it enables reuse through imports and exports.

### Module Definition

In ArkTS, each file is a module. Variables, functions, classes, and interfaces are visible only within the current file by default. Only declarations exported through `export` can be imported by other modules.

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

## export

Using `export`, you can mark declarations in a module as public APIs for other modules to import and reuse as needed. It supports two forms: named exports and default exports.

### Export at Declaration

You can export a variable, constant, function, class, interface, or type alias directly when declaring it.

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

### Unified Export

You can also declare first and then export them together at the end of the file. Unified export is suitable for making the public `API`s of a module visible in one place.

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

### Renamed Export

Use the `export { name as newName }` syntax to rename a binding during export, avoiding naming conflicts or improving API readability.

<!-- @[export_rename](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
class InternalUserService {
  getName(): string {
    return 'UserService';
  }
}

export { InternalUserService as RenamedUserService };
```

### Default Export

A default export uses `export default` to export the module's main functionality, which can be imported under any name.

<!-- @[default_export](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Logger.ets) -->

``` TypeScript
// Logger.ets
export default class Logger {
  info(message: string): void {
    console.info(`${message}`);
  }
}
```

In another file, you can use this class through a default import.

<!-- @[default_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/DefaultImport.ets) -->

``` TypeScript
import Logger from '../common/Logger';

let logger: Logger = new Logger();
logger.info('module loaded');
```
In large projects, public APIs generally prefer named exports, because named exports offer clear advantages in code search, refactoring and maintenance, and interface constraints.

### Re-export

Re-export is commonly used in module entry files to aggregate multiple files in the same domain into a stable entry point.

<!-- @[submodule_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
export interface User {
  id: number;
  name: string;
}
```

Define a service class in another source file to provide business methods.

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

Then aggregate these scattered exports into a unified entry point through a barrel file.

<!-- @[barrel_file_reexport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
export { User } from '../common/Types';
export { UserService } from '../common/Service';
```

Consumers can import from the barrel file without knowing each member's source file. Importing from a barrel file parses and executes modules along the entire dependency chain. For performance-sensitive scenarios, see [Optimizing Performance with import Path Expansion](../arkts-utils/arkts-module-side-effects.md#optimizing-performance-with-import-path-expansion).

<!-- @[barrel_file_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/BarrelFileImport.ets) -->

``` TypeScript
import { User, UserService } from '../common/User';

let service: UserService = new UserService();
let user: User | null = service.findById(1);
console.info(`${user ? user.name : 'not found'}`);
```

## Static Import

Use `import` to bring in bindings exported by other modules and use their types, functions, or classes in the current file. Both named imports and namespace imports are supported.

### Named Import

Use `import { name } from 'path'` to import the named exports of a module by name. You can list multiple bindings within the braces.

<!-- @[named_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/NamedImport.ets) -->

``` TypeScript
import { UserService } from '../common/User';

let service: UserService = new UserService();
```

### Renamed Import

Rename an import when its name conflicts with an existing name in the current file, or when renaming improves readability.

<!-- @[import_rename](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ImportRename.ets) -->

``` TypeScript
import { UserService as AccountUserService } from '../common/User';

let service: AccountUserService = new AccountUserService();
```

### Default Import

Use `import Name from 'path'` to import the default export of a module. The name does not need to match the one used at export time.

<!-- @[default_import_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/DefaultImport.ets) -->

``` TypeScript
import Logger from '../common/Logger';

let logger: Logger = new Logger();
```

### Combining Default and Named Imports

Use `import defaultName, { namedName } from 'path'` to import both the default export and named exports in a single statement.

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

On the consumer side, you can import both the default export and named exports at the same time.

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

### Namespace Import

Use `import * as name from 'path'` to collect all named exports of a target module into one object and access them through `name.memberName`.

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

The importing module accesses all members through a shared object prefix.

<!-- @[namespace_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/NamespaceImport.ets) -->

``` TypeScript
import * as MathUtil from '../common/Math';

let sum: number = MathUtil.add(1, 2);
let product: number = MathUtil.multiply(3, 4);
console.info(`${sum}, ${product}`);
```

Namespace imports suit utility modules with many exports when a source prefix is desired at call sites. For everyday use, prefer named imports to import members as needed and make dependencies clearer.

### Side-Effect Import

An `import 'path'` statement without bindings only loads and executes the target module without importing any exports. It suits modules that initialize or register themselves when loaded.

<!-- @[side_effect_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Config.ets) -->

``` TypeScript
// Config.ets: top-level code executes when the module loads.
console.info('Config initialized');

export const APP_LABEL: string = 'DemoApp';
```

The following statement uses no exports from `Config`; it only ensures that its top-level code executes before the current file:

<!-- @[side_effect_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SideEffectImport.ets) -->

``` TypeScript
import '../common/Config';
```

For side effects of module loading and optimization methods, see [Side Effects and Optimization of Module Loading](../arkts-utils/arkts-module-side-effects.md).

<!--RP1--><!--RP1End-->

## Dynamic Import

Use `import()` to load modules on demand at runtime, for example, for conditional loading or deferred initialization.

### Basic Syntax

Dynamic import is used to load modules on demand. It returns a `Promise`, so it is usually used together with `async`/`await`.

<!-- @[dynamic_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
async function loadFeatureLabel(): Promise<string> {
  let moduleObject = await import('../common/Feature');
  return moduleObject.getFeatureLabel();
}
```

The dynamically loaded module exports its members as usual.

<!-- @[dynamic_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Feature.ets) -->

``` TypeScript
export function getFeatureLabel(): string {
  return 'feature';
}
```

### Constraints

Dynamic import paths must remain statically analyzable. For packaging, package splitting, cross-package loading, or runtime permissions, follow HarmonyOS project and runtime constraints. Dynamic `import` also supports on-demand loading of HSP, HAR, and ohpm packages. For scenarios and complete usage, see [Dynamic Import](../arkts-utils/arkts-dynamic-import.md).

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

## Lazy Module Loading

Adding `lazy` to an `import` statement defers execution of the target module until an imported variable is first used, shortening application cold start. During cold start, dependencies are parsed but module source code is not executed. Accessing the variable synchronously triggers module execution. This feature is supported since API version 12.

<!-- @[lazy_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/ModuleSystem.ts) -->

``` TypeScript
// main.ts
import lazy { a } from './mod1';  // Do not execute mod1.ts top-level code during cold start.

export function loadOnDemand(): string {
  return a;  // Load and execute mod1.ts only when a is first used.
}
```

<!-- @[lazy_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/mod1.ts) -->

``` TypeScript
// mod1.ts
export let a = 'mod1 executed';
```

Unlike dynamic imports, lazy loading retains static import syntax at the beginning of the source file and executes synchronously when triggered. For the complete syntax, constraints, and error examples, see [Lazy Import](../arkts-utils/arkts-lazy-import.md).

## Module Path

Module paths specify source file locations for imports and exports. ArkTS supports relative paths (starting with `./` or `../`) and ohpm package names. Relative paths can omit file extensions. To import a module from an ohpm package, use its package name directly, for example, `import { describe } from '@ohos/hypium'`.

### Relative Path

A relative path is suitable for expressing dependencies near the current module.

<!-- @[relative_path_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/RelativePathImport.ets) -->

``` TypeScript
import { User } from '../common/User';
import { AppConfig } from '../config/appConfig';
import { UserRepository } from '../common/Repository';
```

## Module Organization

Manage the exports of multiple modules through the directory structure and barrel files.

### Organize by Domain

Organizing modules by domain groups related functionality together, improving code maintainability.

<!-- @[submodule_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
export interface User {
  id: number;
  name: string;
}
```

Repository classes in the same directory import and use the types described above.

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

Then, a barrel file aggregates and exposes the public APIs of each module.

<!-- @[submodule_barrel_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SubmoduleBarrelFile.ets) -->

``` TypeScript
export { User } from '../common/Types';
export { UserRepository } from '../common/Repository';
```

### Avoiding Circular Dependencies

Circular dependencies complicate the module initialization order. When modules import each other, extract the shared types, constants, or interfaces into a separate module first.

<!-- @[shared_types_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Types.ets) -->

``` TypeScript
// Types.ets
export interface UserIdentity {
  id: number;
}
```

After importing the shared types, other modules can use them without depending on each other directly.

<!-- @[shared_types_usage_profile](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SharedTypesUsage.ets) -->

``` TypeScript
import { UserIdentity } from '../common/Types';

export function getProfileName(identity: UserIdentity): string {
  return 'user-' + identity.id.toString();
}
```

The same shared type can be reused across multiple modules.

<!-- @[shared_types_usage_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/SharedTypesUsage.ets) -->

``` TypeScript
export function canRead(identity: UserIdentity): boolean {
  return identity.id > 0;
}
```

## Top-Level Statements

Top-level statements are code written at the outermost module level, outside functions, classes, or block scopes. They execute from top to bottom when the module first loads and are commonly used for module-level initialization. Imported modules' top-level statements always execute before the importing module's statements.

<!-- @[top_level_statements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/ModuleSystem.ets) -->

``` TypeScript
// Top-level statement of the module
let appConfig: string = 'production';
const MAX_RETRIES: number = 3;

function logConfig(): void {
  console.info(`Config: ${appConfig}, Retries: ${MAX_RETRIES}`);
}

// Top-level expression
console.info('Module loaded');
logConfig();
```

In this example, `console.info('Module loaded')` and `logConfig()` execute immediately when the module loads. `logConfig()` can read `appConfig` and `MAX_RETRIES`, which are declared before it. Keep top-level statements lightweight to avoid slowing module loading with time-consuming initialization. For complete execution rules (loading order, single-execution semantics, cross-thread behavior, and more) and the loading process, see [Overview of Modular Operation](../arkts-utils/module-principle.md). For side effects and optimization, see [Side Effects and Optimization of Module Loading](../arkts-utils/arkts-module-side-effects.md).

## Declaration Files

A declaration file describes a module's external capabilities as a whole. It contains only type and interface declarations (such as `interface` and function signatures), without implementations, for compiler type checking. ArkTS uses `.d.ets` declaration files, similar to TypeScript's `.d.ts` files. Common uses include type declarations exposed by shared packages and type declarations for objects exported by NAPI native modules. During module type resolution, if same-name files with different extensions exist in a directory, `.d.ets` takes priority over `.d.ts` by default.

Use `declare` in a declaration file for entities implemented elsewhere. It tells the compiler that the implementation file or native library provides the entity, while the current file describes only its type. For example, `declare const` declares a constant defined by another module or native library, `declare function` declares a function implemented elsewhere, and `export declare` both declares and exports an entity:

<!-- @[declaration_file_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/common/Declaration.d.ets) -->

``` TypeScript
// common/Declaration.d.ets: declaration files contain declarations only, not implementations.
declare const APP_VERSION: string;

declare function logConfig(): void;

declare class ConfigReader {
  read(key: string): string | undefined;
}

export declare function getConfig(name: string): string;
```
