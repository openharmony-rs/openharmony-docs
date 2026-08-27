# CustomEnvKey

自定义环境变量的Key的类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
protected constructor()
```

用于创建该类的实例对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// 使用WrappedBuilder封装myBuilder
let builderVar: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(myBuilder);
```

## create

```TypeScript
static create<T>(): CustomEnvKey<T>
```

创建一个自定义环境变量Key，作为\@CustomEnv装饰器的参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomEnvKey](arkts-arkui-customenvkey-c.md)&lt;T&gt; | 自定义环境变量Key，用于标识要获取的自定义环境变量。 |

## type

```TypeScript
private type?: S
```

自定义环境变量Key的类型。

**类型：** S

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
