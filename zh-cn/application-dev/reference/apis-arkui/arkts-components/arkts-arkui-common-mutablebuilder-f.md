# mutableBuilder

## mutableBuilder

```TypeScript
declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>
```

`mutableBuilder`是一个泛型函数，它返回一个`MutableBuilder`对象，只接受一个全局的`@Builder`函数作为其参数。 `mutableBuilder`函数返回的[MutableBuilder](arkts-arkui-mutablebuilder-c.md#MutableBuilder)对象，其`builder`属性方法只能在自定义组件的`build`函数或`@Builder`装饰的函数内部被调用。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>--><!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [BuilderCallback](arkts-arkui-buildercallback-t.md) | 是 | `@Builder`装饰的全局函数，作为`mutableBuilder`封装的目标构建函数。该函数需符合`BuilderCallback`类型，即 `(...args: Args) => void`，是一个无返回值的函数，其参数列表`...args`的类型由泛型`Args`指定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableBuilder](arkts-arkui-mutablebuilder-c.md)&lt;Args&gt; | `MutableBuilder&lt;Args&gt;`的实例，用于封装全局` |

