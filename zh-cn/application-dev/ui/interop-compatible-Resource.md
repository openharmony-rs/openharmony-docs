# ArkTS1.2使用ArkTS1.1 Resource

## 概述

从API version 20开始，[Resource](../reference/apis-arkui/arkui-ts/ts-types.md)对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用Resource对象的场景。

## 架构原理

在互操作场景下，支持在ArkTS1.1创建的Resouece对象传递到ArkTS1.2。

## 设计理念

Resource对象互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。

- 渐进式迁移：逐步将ArkTS1.1命令式节点迁移到新版本。

- 使用旧Resource对象：使用稳定的ArkTS1.1 Resource对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

## 开发场景

### 在ArkTS1.2引用ArkTS1.1中创建的Resource对象。

通过在ArkTS1.2中引用ArkTS1.1创建的Resource对象显示Text文本。

示例如下：

- 创建ArkTS1.1子模块`library`，在`library/src/main/ets/components`目录创提创建ArkTS1.1Resource的方法。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets

  export function rawFileTest() {
    return $rawfile('startIcon.png');
  }

  export function resourceTest(): Object {
    return $r('app.float.image_size');
  }
  ```
  ```TypeScript
  // library/Index.ets

  export { resourceTest, rawFileTest} from './src/main/ets/components/MainPage';
  ```


- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    "library": "file:../library"
  }
  ```

- 在ArkTS1.2主模块中引入ArkTS1.1 Resource对象。

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets
  
  import { Entry, Column, Component, Resource, Image } from '@ohos.arkui.component';
  import transfer from '@ohos.transfer';
  import { resourceTest, rawFileTest } from 'library';

  // Resource $r对象互操作
  export function resourceTrans(): Resource {
  
     let resourceDynamic = resourceTest();

     return transfer.transferStatic(resourceDynamic, 'Global.Resource')! as Resource;

  }
  // Resource RawFile对象互操作
  export function rawFileTrans(): Resource {
    let resourceDynamic = rawFileTest();
    return transfer.transferStatic(resourceDynamic, 'Global.Resource')! as Resource;
  }
  
  @Entry
  @Component
  struct MyStateSample {
    build() {
      Column(undefined) {
        Image(rawFileTrans())
          .size({width:resourceTrans(), height:resourceTrans()})
      }
    }
  }
  ```
  ![image](figures/resourceTransfer.png)

### 完整示例结构

完整代码结构树如下图所示。

```text
project/
├── entry/          # ArkTS1.2主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library/         # ArkTS1.1子模块
    └── src/
       ├── main/
       │     ├── ets/
       │     │  └── components/
       │     │    └── MainPage.ets
       │     └── resources/
       │        └── rawfile/
       │          └── startIcon.png
       └── Index.ets
```
