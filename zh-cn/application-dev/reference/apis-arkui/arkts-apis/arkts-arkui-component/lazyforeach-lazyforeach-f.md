# LazyForEach

## LazyForEach

```TypeScript
export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,
    itemGenerator: ItemGeneratorFunc<T>,
    keyGenerator?: KeyGeneratorFunc<T>,
): LazyForEachAttribute
```

输入值以获取带有选项的LazyForEach。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): LazyForEachAttribute--><!--Device-unnamed-export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 要在UI中使用的数组集合。 |
| itemGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | item生成器函数。 |
| keyGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 否 | 密钥生成器函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | LazyForEach组件。 |


## LazyForEach

```TypeScript
export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,
    itemGenerator: ItemGeneratorFunc<T>,
    keyGenerator?: KeyGeneratorFunc<T>,
    options?: LazyForEachOptions,
): LazyForEachAttribute
```

输入值以获取带有选项的LazyForEach。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,    options?: LazyForEachOptions,): LazyForEachAttribute--><!--Device-unnamed-export declare function LazyForEach<T = Any>(dataSource: IDataSource<T>,    itemGenerator: ItemGeneratorFunc<T>,    keyGenerator?: KeyGeneratorFunc<T>,    options?: LazyForEachOptions,): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSource | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 要在UI中使用的数组集合。 |
| itemGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | item生成器函数。 |
| keyGenerator | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 否 | 密钥生成器函数。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | LazyForEach可选参数选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | LazyForEach组件 |


## LazyForEach

```TypeScript
export declare function LazyForEach<T = Any>(
    style: CustomBuilderT<LazyForEachAttribute>
): LazyForEachAttribute
```

定义LazyForEach组件。它需要在组件属性设置开始时调用setLazyForEachOptions。 并且它需要在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function LazyForEach<T = Any>(    style: CustomBuilderT<LazyForEachAttribute>): LazyForEachAttribute--><!--Device-unnamed-export declare function LazyForEach<T = Any>(    style: CustomBuilderT<LazyForEachAttribute>): LazyForEachAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 回调来设置LazyForEach的属性 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | LazyForEach的属性。 |

