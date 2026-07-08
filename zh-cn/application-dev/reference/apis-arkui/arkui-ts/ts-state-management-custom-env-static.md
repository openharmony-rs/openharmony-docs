# \@CustomEnv：自定义环境变量 (ArkTS-Sta)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @songyanhong-->
<!--Adviser: @zhang_yixin13-->

\@CustomEnv装饰器，支持环境变量自定义能力。

在ArkTS-Sta中使用时，开发者指南见：[\@CustomEnv开发者指南](../../../ui/state-management-static/arkts-static-custom-env-property.md)。

**ArkTS-Sta起始版本：** 26.0.0

> **说明：**
>
> 本模块仅适用于ArkTS-Sta。

## @CustomEnv

@interface CustomEnv

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
'use static'

import { Entry, ComponentV2, CustomEnv, CustomEnvKey, Column } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  // @CustomEnv装饰的变量设置本地默认值
  @CustomEnv('custom') customVarName: string = 'hello world';

  build() {
    Column() {
    }
  }
}
```

## CustomEnvKey\<S\>

自定义环境变量的Key的类型。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

### create\<T\>

static create\<T\>()

用于创建自定义环境变量Key的实例。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

### constructor

protected constructor()

CustomEnvKey构造方法。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

**示例：**

```ts
'use static'

import { Entry, ComponentV2, CustomEnv, CustomEnvKey, Column } from '@kit.ArkUI';

const custom = CustomEnvKey.create<string>();

@Entry
@ComponentV2
struct Index {
  @CustomEnv('custom') customVarName: string = 'hello world';

  build() {
    Column() {
    }
  }
}
```