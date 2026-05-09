# \@CustomEnv：自定义环境变量
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
> 
> 本模块首批接口从API version 26.0.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

[\@CustomEnv](#customenv)用于读取由[WithEnv](ts-container-with-env.md)作用域通过[customEnv](ts-container-with-env.md#customenv)设置的自定义环境变量。如需读取系统环境变量，请参考[@Env：环境变量](ts-env-system-property.md)。

## \@CustomEnv
CustomEnv: CustomEnvDecorator

**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

|名称|类型|说明|
| ----- | ----- | ------ |
|CustomEnv|[CustomEnvDecorator](#customenvdecorator)| 自定义环境变量装饰器。 |

**示例：**

```ts
@Component
struct TitleCard {
  @CustomEnv('card.title') title: string = '默认标题';

  build() {
    Text(this.title)
  }
}

@Entry
@Component
struct Index {
  @State outerTitle: string = '外层标题';

  build() {
    Column({ space: 12 }) {
      TitleCard()
      WithEnv() {
        Column({ space: 12 }) {
          TitleCard()
          WithEnv() {
            TitleCard()
          }
          .customEnv('card.title', '内层标题')
        }
      }
      .customEnv('card.title', this.outerTitle)
    }
  }
}
```

## CustomEnvDecorator
type CustomEnvDecorator = (value: string) => PropertyDecorator

定义\@CustomEnv装饰器类型。

**模型约束**：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型   | 必填 | 说明          |
| -------- | ------ | ---- | --------- |
| value    | string | 是   | 自定义环境变量名称。 |

**返回值：**

|类型|说明|
| ----- | ----- |
| PropertyDecorator| 属性装饰器。 |

> **说明：**
>
> - \@CustomEnv只能声明在[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)或[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)装饰的自定义组件中。
> - \@CustomEnv会读取最近祖先[WithEnv](ts-container-with-env.md)作用域中通过[customEnv](ts-container-with-env.md#customenv)设置的同名值。
> - 当未命中对应的WithEnv自定义环境变量时，返回属性声明时设置的本地默认值。
> - \@CustomEnv属性在组件构造完成后为只读，不支持直接赋值。
