# \@CustomEnv：自定义环境变量
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @songyanhong-->
<!--Adviser: @zhang_yixin13-->

用于获取自定义环境变量。

开发者指南见：[\@CustomEnv开发者指南](../../../ui/arkts-custom-env-property.md)。

**起始版本：** 26.0.0

## \@CustomEnv
CustomEnv\<T\>(key: CustomEnvKey\<S\>): PropertyDecorator

\@CustomEnv装饰器，支持环境变量自定义能力。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

|名称|类型|说明|
| ----- | ----- | ------ |
|CustomEnv|PropertyDecorator| 自定义环境变量装饰器。|

**示例：**

```ts
@Entry
@Component
struct Index {
  // @CustomEnv装饰的变量设置本地默认值
  @CustomEnv(custom) customVarName: string = 'hello world';

  build() {
  }
}
```

## CustomEnvKey\<S\>

自定义环境变量的Key的类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**


| 名称 | 类型 | 只读 | 可选 | 说明                                                                                              |
| -------- | -------- | -------- | -------- |-------------------------------------------------------------------------------------------------|
| type | S | 否 | 是 | 自定义环境变量Key对应的类型。|


### create\<T\>

static create\<T\>()

创建一个自定义环境变量Key，作为\@CustomEnv装饰器的参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

protected constructor()

用于创建该类的实例对象。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
const custom = CustomEnvKey.create<string>();
@CustomEnv(custom) message: string = 'hello world';
```