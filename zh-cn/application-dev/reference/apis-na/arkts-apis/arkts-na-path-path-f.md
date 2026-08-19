# Path

## Path

```TypeScript
@ComponentBuilder
export declare function Path(
    options?: PathOptions
): PathAttribute
```

路径绘制组件，根据绘制路径生成封闭的自定义形状。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Path(    options?: PathOptions): PathAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Path(    options?: PathOptions): PathAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PathOptions](arkts-na-path-pathoptions-i.md) | 否 | Path绘制区域。 <br>异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathAttribute](arkts-na-path-pathattribute-i.md) |  |


## Path

```TypeScript
@Builder
export declare function Path(
    style: CustomBuilderT<PathAttribute>,
): PathAttribute
```

Defines Path Component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Path(    style: CustomBuilderT<PathAttribute>,): PathAttribute--><!--Device-unnamed-@Builderexport declare function Path(    style: CustomBuilderT<PathAttribute>,): PathAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[PathAttribute](arkts-na-path-pathattribute-i.md)&gt; | 是 | the callback to set up component's attributes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathAttribute](arkts-na-path-pathattribute-i.md) |  |

