# wrapBuilder

## wrapBuilder

```TypeScript
export declare function wrapBuilder<T>(builder: T): WrappedBuilder<T>
```

wrapBuilder是一个模板函数，返回一个`WrappedBuilder`对象。模板参数`T`是@Builder的函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function wrapBuilder<T>(builder: T): WrappedBuilder<T>--><!--Device-unnamed-export declare function wrapBuilder<T>(builder: T): WrappedBuilder<T>-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | T | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WrappedBuilder&lt;T&gt; | WrappedBuilder对象。 |

