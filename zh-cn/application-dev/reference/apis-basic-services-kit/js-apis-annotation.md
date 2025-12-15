# @ohos.annotation (注解)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Base-->
<!--Owner: @majiajun518-->
<!--Designer: @majiajun518-->
<!--Tester: @jiyong_sd-->
<!--Adviser: @fang-jinxu-->

本模块定义了OpenHarmony ArkTS API的注解类型，如生命周期最小可用版本等。

> **说明：**
>
> - 本模块首批接口从 API version 22 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```typescript
import { Available, SuppressWarnings, SuppressWarningsType } from '@kit.BasicServicesKit';
```

## Available

@interface Available {
  minApiVersion: string = ''
}

系统提供的API注解能力，可用于标记API支持的最低可用版本。此注解可以标注在类、接口、变量、类型、模块、枚举等API上。在源码定义处添加注解后，编译工具会在使用处检查潜在的兼容性问题。当minApiVersion大于build-profile.json5中指定的compatibleSDKVersion字段，会生成兼容性警告。

**卡片能力：** 从API version 22开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base

| 名称 | 类型 | 只读 | 可选 | 说明                       |
| ---- | ---- | ---- | --- | -------------------------- |
| minApiVersion | string | 否 | 否 | minApiVersion用于标识最低可用版本，由两部分组成：系统类型+版本号。仅当系统类型为OpenHarmony时可省略系统类型。例如：'OpenHarmony 20'，'20'。 |

**示例：**

  ```typescript
  import { Available } from '@kit.BasicServicesKit';

  @Available({minApiVersion: 'OpenHarmony 22'})
  function myFunc() {}

  @Available({minApiVersion: '22'}) //OpenHarmony default
  class MyClass {}
  ```


## SuppressWarnings<sup>23+<sup>

@interface SuppressWarnings {
  rules: Array\<SuppressWarningsType>;
}

系统提供的API注解能力，可以用于消除API产生的告警。此注解可以标注在类、函数、变量、类型、接口等API上。在源码用此注解后，编译时会根据配置的规则来抑制对应警告。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Base

| 名称 | 类型 | 只读 | 可选 | 说明                       |
| ---- | ---- | ---- | --- | -------------------------- |
| rules | Array<[SuppressWarningsType](#suppresswarningstype23)> | 否 | 否 | 支持告警消除的规则集合|

**示例：**
  ```typescript
  import { SuppressWarnings, SuppressWarningsType } from '@kit.BasicServicesKit';

  @SuppressWarnings({rules: [SuppressWarningsType.COMPATIBILITY]})
  function myFunc() {}
  ```


## SuppressWarningsType<sup>23+<sup>

支持消除告警的规则。

**系统能力：** SystemCapability.Base

| 名称                   | 值   | 说明                           |
| ---------------------- | ---- | ------------------------------ |
| COMPATIBILITY     | compatibility    | 支持消除兼容性告警。 |
