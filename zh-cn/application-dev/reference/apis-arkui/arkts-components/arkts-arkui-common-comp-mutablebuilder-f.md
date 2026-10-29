# mutableBuilder

## mutableBuilder

```TypeScript
declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>
```

使用`mutableBuilder`封装全局[\@Builder](arkts-arkui-common-comp-builder-d.md#builder)，以支持在运行时根据不同条件动态切换全局`@Builder`内容（如根据状态切换不同的UI构建逻辑）。开发指南参考：[mutableBuilder：实现全局@Builder动态更新](../../../ui/state-management/arkts-mutableBuilder.md)。

`mutableBuilder`是一个泛型函数，它返回一个`MutableBuilder`对象，只接受一个全局的`@Builder`函数作为其参数。

`mutableBuilder`函数返回的[MutableBuilder](arkts-arkui-common-comp-mutablebuilder-c.md)对象，其`builder`属性方法只能在自定义组件的`build`函数或`@Builder`装饰的函数内部被调用。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>--><!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [BuilderCallback](arkts-arkui-common-comp-buildercallback-t.md) | 是 | `@Builder`装饰的全局函数，作为`mutableBuilder`封装的目标构建函数。该函数需符合`BuilderCallback`类型，即`(...args: Args) =&gt; void`，是一个无返回值的函数，其参数列表`...args`的类型由泛型`Args`指定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableBuilder](arkts-arkui-common-comp-mutablebuilder-c.md)&lt;Args&gt; | `MutableBuilder<Args>`的实例，用于封装全局`@Builder`函数，并支持在运行时动态切换构建逻辑。该实例持有对全局`@Builder`函数的引用，可通过其`builder`属性调用被封装的构建函数，或通过重新赋值`mutableBuilder`函数返回的新实例动态切换构建逻辑。其`builder`属性方法只能在自定义组件的`build`函数或`@Builder`装饰的函数内部被调用。 |
