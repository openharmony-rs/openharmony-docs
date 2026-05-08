# 复用选项

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

reuse属性用于给\@ReusableV2装饰的自定义组件指定复用选项。

本文档仅为API参考说明。实际功能使用与限制见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## reuse

ArkTS-Dyn: reuse(options: ReuseOptions): T

ArkTS-Sta: reuse(options: ReuseOptions | undefined): this

复用选项，用于设置V2自定义组件的复用选项。

>  **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名  | 类型                          | 必填 | 说明                                           |
| ------- | ----------------------------- | ---- | ---------------------------------------------- |
| options | ArkTS-Dyn: [ReuseOptions](#reuseoptions)<br/>ArkTS-Sta: [ReuseOptions](#reuseoptions) \| undefined | 是   | 复用选项，用于配置复用相关信息，由开发者指定。 |

**返回值：** 

| 类型                          | 说明                                           |
| ----------------------------|---------------------------------------------- |
|   ArkTS-Dyn: T <br/> ArkTS-Sta: this |   返回当前组件。 |

## ReuseOptions

复用选项信息。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

### 属性

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------- | ----------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| reuseId | [ReuseIdCallback](#reuseidcallback) | 否 | 是 | 复用标识id，相同复用标识id的V2自定义组件会被互相复用。默认的复用标识id为自定义组件名。<br>在API版本26.0.0之前，当reuseId不是显式返回字符串字面量的回调方法时，实际的复用标识id为该自定义组件的名称。例如，`Child().reuse({ reuseId: () => getReuseId() })`的实际复用标识为`"Child"`。<br>在API版本26.0.0及以后，支持将非显式返回字符串字面量形式的reuseId作为实际的复用标识id。例如，`Child().reuse({ reuseId: () => getReuseId() })`的实际复用标识为`getReuseId()`的返回结果。 |

## ReuseIdCallback

type ReuseIdCallback = () => string

获取复用标识id的回调方法。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| string | 复用标识id，由开发者指定。<br>未指定或使用空字符串`''`作为复用标识id时，将默认使用自定义组件名。 |

## 示例

ArkTS-Dyn示例：

```ts
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // 使用'reuseComponent'作为reuseId
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // 使用空字符串将默认使用组件名'ReusableV2Component'作为reuseId
      ReusableV2Component() // 未指定reuseId将默认使用组件名'ReusableV2Component'作为reuseId
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
  }
}
```


ArkTS-Sta示例：

```ts
'use static'
import { Entry, ComponentV2, Column, ReusableV2 } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // 使用'reuseComponent'作为reuseId
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // 使用空字符串将默认使用组件名'ReusableV2Component'作为reuseId
      ReusableV2Component() // 未指定reuseId将默认使用组件名'ReusableV2Component'作为reuseId
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
  }
}
```
