# ForEach

## ForEach

```TypeScript
@ComponentBuilder
export declare function ForEach<T = Any>(arr: Array<T>,
    itemGenerator: ItemGeneratorFunc<T>,
    keyGenerator?: KeyGeneratorFunc<T>,
): ForEachAttribute
```

定义ForEach组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function ForEach<T = Any>(arr: Array<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): ForEachAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ForEach<T = Any>(arr: Array<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): ForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | Array&lt;T&gt; | 是 | 在UI中使用的数组集合。 |
| itemGenerator | [ItemGeneratorFunc](arkts-na-itemgeneratorfunc-t.md)&lt;T&gt; | 是 | 项生成函数。 |
| keyGenerator | [KeyGeneratorFunc](arkts-na-keygeneratorfunc-t.md)&lt;T&gt; | 否 | 键生成函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ForEachAttribute | ForEach的属性。 |


## ForEach

```TypeScript
@Builder
export declare function ForEach(
    style: CustomBuilderT<ForEachAttribute>
): ForEachAttribute
```

定义ForEach组件。需要在组件属性设置开始时调用setForEachOptions，并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ForEach(    style: CustomBuilderT<ForEachAttribute>): ForEachAttribute--><!--Device-unnamed-@Builderexport declare function ForEach(    style: CustomBuilderT<ForEachAttribute>): ForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ForEachAttribute&gt; | 是 | 用于设置ForEach属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ForEachAttribute | ForEach属性实例。 |

