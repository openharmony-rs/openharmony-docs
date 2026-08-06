# PluginComponent（系统接口）

## PluginComponent

```TypeScript
export declare function PluginComponent(
    options: PluginComponentOptions
): PluginComponentAttribute
```

创建插件组件，用于显示外部应用提供的UI。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function PluginComponent(    options: PluginComponentOptions): PluginComponentAttribute--><!--Device-unnamed-export declare function PluginComponent(    options: PluginComponentOptions): PluginComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 定义用于构造插件组件的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## PluginComponent

```TypeScript
export declare function PluginComponent(
    style: CustomBuilderT<PluginComponentAttribute>
): PluginComponentAttribute
```

定义PluginComponent组件。它要求在组件属性设置开始时调用setPluginComponentOptions， 并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function PluginComponent(    style: CustomBuilderT<PluginComponentAttribute>): PluginComponentAttribute--><!--Device-unnamed-export declare function PluginComponent(    style: CustomBuilderT<PluginComponentAttribute>): PluginComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置plugincomponent属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | PluginComponent的属性。 |

