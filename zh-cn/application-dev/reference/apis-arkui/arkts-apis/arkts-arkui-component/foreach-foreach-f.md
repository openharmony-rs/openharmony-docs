# ForEach

## ForEach

```TypeScript
export declare function ForEach<T = Any>(arr: Array<T>,
    itemGenerator: ItemGeneratorFunc<T>,
    keyGenerator?: KeyGeneratorFunc<T>,
): ForEachAttribute
```

定义ForEach组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ForEach<T = Any>(arr: Array<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): ForEachAttribute--><!--Device-unnamed-export declare function ForEach<T = Any>(arr: Array<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): ForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | Array&lt;T&gt; | 是 | 在UI中使用的数组集合。 |
| itemGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 项生成函数。 |
| keyGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 否 | 键生成函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | ForEach的属性。 |


## ForEach

```TypeScript
export declare function ForEach(
    style: CustomBuilderT<ForEachAttribute>
): ForEachAttribute
```

定义ForEach组件。需要在组件属性设置开始时调用setForEachOptions，并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function ForEach(    style: CustomBuilderT<ForEachAttribute>): ForEachAttribute--><!--Device-unnamed-export declare function ForEach(    style: CustomBuilderT<ForEachAttribute>): ForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置ForEach属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | ForEach属性实例。 |

