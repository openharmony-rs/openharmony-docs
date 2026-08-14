# wrapBuilder

## wrapBuilder

```TypeScript
declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>
```

`wrapBuilder`用于封装全局@Builder，可以将全局`@Builder`函数作为参数传递，实现按引用传递和动态调用，提升代码复用性。 开发指南见：[wrapBuilder：封装全局@Builder](../../../ui/state-management/arkts-wrapBuilder.md)。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>--><!--Device-unnamed-declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | 是 | `@Builder`装饰的全局函数，传入后将被封装为`WrappedBuilder`对象。该函数必须是无返回值（`void`）的函数，其参数列表`...args`的类型和顺序 由泛型`Args`定义。当需要在组件间按引用传递或复用某个全局`@Builder`函数时传入此参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WrappedBuilder](arkts-arkui-wrappedbuilder-c.md)&lt;Args&gt; | `WrappedBuilder&lt;Args&gt;`的实例，用于在组件之间复用或传递全局` |

