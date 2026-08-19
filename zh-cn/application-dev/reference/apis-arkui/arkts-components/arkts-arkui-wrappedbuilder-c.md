# WrappedBuilder

`WrappedBuilder`是`@Builder`函数的包装类，用于封装全局`@Builder`函数及其参数，实现按引用传递和动态调用。

**起始版本：** 11

<!--Device-unnamed-declare class WrappedBuilder--><!--Device-unnamed-declare class WrappedBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(builder: (...args: Args) => void)
```

`WrappedBuilder`的构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WrappedBuilder-constructor(builder: (...args: Args) => void)--><!--Device-WrappedBuilder-constructor(builder: (...args: Args) => void)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | 是 | `@Builder`装饰的全局函数，作为构造参数用于初始化`WrappedBuilder`实例。函数参数`args`为该`@Builder`函数所需的参数列表。 |

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

## builder

```TypeScript
builder: (...args: Args) => void
```

`@Builder`装饰的全局函数，用于生成对应的自定义构建内容。

**类型：** (...args: Args) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WrappedBuilder-builder: (...args: Args) => void--><!--Device-WrappedBuilder-builder: (...args: Args) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

