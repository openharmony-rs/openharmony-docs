# DynamicComponent（系统接口）

## DynamicComponent

```TypeScript
@ComponentBuilder
export declare function DynamicComponent(
    options: DynamicOptions
): DynamicComponentAttribute
```

创建DynamicComponent组件，用于显示Worker线程中运行的Abc UI。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function DynamicComponent(    options: DynamicOptions): DynamicComponentAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function DynamicComponent(    options: DynamicOptions): DynamicComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DynamicOptions](arkts-na-dynamiccomponent-dynamicoptions-i-sys.md) | 是 | DynamicComponent的构造配置参数，用于配置要加载的Abc页面入口、运行Worker及显示选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DynamicComponentAttribute](arkts-na-dynamiccomponent-dynamiccomponentattribute-i.md) |  |


## DynamicComponent

```TypeScript
@Builder
export declare function DynamicComponent(
    style: CustomBuilderT<DynamicComponentAttribute>
): DynamicComponentAttribute
```

定义DynamicComponent组件。要求在组件属性设置开始时调用setDynamicComponentOptions， 在组件属性设置结束时 调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function DynamicComponent(    style: CustomBuilderT<DynamicComponentAttribute>): DynamicComponentAttribute--><!--Device-unnamed-@Builderexport declare function DynamicComponent(    style: CustomBuilderT<DynamicComponentAttribute>): DynamicComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[DynamicComponentAttribute](arkts-na-dynamiccomponent-dynamiccomponentattribute-i.md)&gt; | 是 | 用于设置DynamicComponent属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DynamicComponentAttribute](arkts-na-dynamiccomponent-dynamiccomponentattribute-i.md) | DynamicComponent的属性。 |

