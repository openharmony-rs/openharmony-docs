# If

## If

```TypeScript
@ComponentBuilder
export declare function If(
  condition: boolean,
  content_: CustomBuilder
): IfAttribute
```

定义If组件

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function If(  condition: boolean,  content_: CustomBuilder): IfAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function If(  condition: boolean,  content_: CustomBuilder): IfAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | boolean | 是 | 'If'分支对应的条件 |
| content_ | CustomBuilder | 是 | 'If'分支需要运行的代码 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IfAttribute](arkts-na-if-ifattribute-i.md) |  |


## If

```TypeScript
@Builder
export declare function If(
    style: CustomBuilderT<IfAttribute>,
    content_: CustomBuilder
): IfAttribute
```

定义If组件。它需要在组件属性设置开始时调用setIfOptions。 并且它需要在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function If(    style: CustomBuilderT<IfAttribute>,    content_: CustomBuilder): IfAttribute--><!--Device-unnamed-@Builderexport declare function If(    style: CustomBuilderT<IfAttribute>,    content_: CustomBuilder): IfAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[IfAttribute](arkts-na-if-ifattribute-i.md)&gt; | 是 | 回调来设置If的属性 |
| content_ | CustomBuilder | 是 | 分支的逻辑代码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IfAttribute](arkts-na-if-ifattribute-i.md) | If的属性。 |

